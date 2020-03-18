---
title: Protobuf hesaplamaları - WCF geliştiricileri için gRPC
description: Protobuf'ta sayısallaştırmaları nasıl beyan edin ve kullanacağınızı öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148081"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="ffa9d-103">Protobuf sabit listeleri</span><span class="sxs-lookup"><span data-stu-id="ffa9d-103">Protobuf enumerations</span></span>

<span data-ttu-id="ffa9d-104">Protobuf numaralandırma türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="ffa9d-105">Bu desteği, bir `Oneof` alanın türünü belirlemek için bir enumun kullanıldığı önceki bölümde gördünuz.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="ffa9d-106">Kendi numaralandırma türlerinizi tanımlayabilirsiniz ve Protobuf bunları C# enum türlerine derler.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span>

<span data-ttu-id="ffa9d-107">Protobuf'u çeşitli dillerde kullanabileceğinizden, numaralandırmaiçin adlandırma kuralları C# kurallarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="ffa9d-108">Ancak, kod üreteci adları geleneksel C# örneğine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="ffa9d-109">Alan adının Pascal-case eşdeğeri numaralandırma adı ile başlarsa, o zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="ffa9d-110">Örneğin, aşağıdaki Protobuf numaralandırmasında, alanlar `ACCOUNT_STATUS`.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="ffa9d-111">Bu önek Pascal-case enum adı, `AccountStatus`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="ffa9d-112">Jeneratör aşağıdaki koda eşdeğer bir C# enum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ffa9d-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="ffa9d-113">Protobuf numaralandırma tanımları ilk alanları olarak sıfır *sabitolmalıdır.*</span><span class="sxs-lookup"><span data-stu-id="ffa9d-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="ffa9d-114">C#'da olduğu gibi, aynı değere sahip birden çok alanı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="ffa9d-115">Ancak, enumdaki `allow_alias` seçeneği kullanarak bu seçeneği açıkça etkinleştirmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="ffa9d-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="ffa9d-116">Bir `.proto` dosyada en üst düzeyde ki tümumerations'ı bildirebilir veya ileti tanımı içinde iç içe.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="ffa9d-117">İç içe geçmiş iletiler gibi iç içe geçmiş yinelemeler, oluşturulan ileti sınıfındaki `.Types` statik sınıf içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="ffa9d-118">[[Bayraklar]](xref:System.FlagsAttribute) özniteliğini Protobuf tarafından oluşturulan bir enuma uygulamanın bir yolu yoktur ve Protobuf bitwise enum kombinasyonlarını anlamaz.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="ffa9d-119">Aşağıdaki örneğe bakın:</span><span class="sxs-lookup"><span data-stu-id="ffa9d-119">Look at the following example:</span></span>

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

<span data-ttu-id="ffa9d-120">Ayarlarsanız, `product.AvailableIn` bu sayı, tümsado değeri `3`olarak serihale edilir. `Region.NorthAmerica | Region.SouthAmerica`</span><span class="sxs-lookup"><span data-stu-id="ffa9d-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="ffa9d-121">Bir istemci veya sunucu değeri deserialize etmeye çalıştığında, enum tanımında bir `3`eşleşme bulamaz.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="ffa9d-122">Sonuç. `Region.None`</span><span class="sxs-lookup"><span data-stu-id="ffa9d-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="ffa9d-123">Protobuf'ta birden çok enum değeriyle çalışmanın `repeated` en iyi yolu, enum türünde bir alan kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ffa9d-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ffa9d-124">[Önceki](protobuf-any-oneof.md)
>[Sonraki](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="ffa9d-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
