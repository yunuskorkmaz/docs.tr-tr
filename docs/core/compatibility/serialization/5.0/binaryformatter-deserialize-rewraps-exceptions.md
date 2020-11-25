---
title: 'Son değişiklik: BinaryFormatter. serisini kaldırma bazı özel durumları yeniden kaydırır'
description: BinaryFormatter. serisini kaldırma, bir SerializationException içindeki bazı özel durum nesnelerini yeniden sarmaladığı .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 08/18/2020
ms.openlocfilehash: 90dc4cce6785fdb38644cca2a2e9aff65eb7a313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761433"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="cb7d0-103">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="cb7d0-103">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="cb7d0-104"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Yöntemi artık <xref:System.Runtime.Serialization.SerializationException> özel durumu çağırana geri yaymadan önce bir içindeki bazı özel durum nesnelerini yeniden sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="cb7d0-104">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

## <a name="change-description"></a><span data-ttu-id="cb7d0-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="cb7d0-105">Change description</span></span>

<span data-ttu-id="cb7d0-106">Daha önce, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> yöntemi gibi bazı rastgele özel durumlara izin veriliyordu <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="cb7d0-106">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="cb7d0-107">.NET 5,0 ve sonraki sürümlerde yöntemi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> geçersiz seri hale getirmeler işlemleri nedeniyle oluşan özel durumları yakalar ve bunları bir içinde kaydırır <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="cb7d0-107">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="cb7d0-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="cb7d0-108">Version introduced</span></span>

<span data-ttu-id="cb7d0-109">5.0</span><span class="sxs-lookup"><span data-stu-id="cb7d0-109">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="cb7d0-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cb7d0-110">Recommended action</span></span>

<span data-ttu-id="cb7d0-111">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cb7d0-111">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="cb7d0-112">Ancak, çağrı siteniz oluşan belirli bir özel duruma bağlıysa, <xref:System.Runtime.Serialization.SerializationException> Aşağıdaki örnekte gösterildiği gibi, özel durumu dıştaki öğesinden geri sardırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb7d0-112">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a><span data-ttu-id="cb7d0-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cb7d0-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
