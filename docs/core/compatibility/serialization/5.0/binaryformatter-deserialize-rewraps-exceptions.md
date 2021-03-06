---
title: 'Son değişiklik: BinaryFormatter. serisini kaldırma bazı özel durumları yeniden kaydırır'
description: BinaryFormatter. serisini kaldırma, .NET 5 ' teki son değişiklik hakkında bilgi edinmek için bir SerializationException içindeki bazı özel durum nesnelerini yeniden sarmalar.
ms.date: 08/18/2020
ms.openlocfilehash: 8e357035908f34c6c5c77d2a0728ab213bdc791a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256354"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="356a4-103">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="356a4-103">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="356a4-104"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Yöntemi artık <xref:System.Runtime.Serialization.SerializationException> özel durumu çağırana geri yaymadan önce bir içindeki bazı özel durum nesnelerini yeniden sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="356a4-104">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

## <a name="change-description"></a><span data-ttu-id="356a4-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="356a4-105">Change description</span></span>

<span data-ttu-id="356a4-106">Daha önce, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> yöntemi gibi bazı rastgele özel durumlara izin veriliyordu <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="356a4-106">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="356a4-107">.NET 5 ve sonraki sürümlerde yöntemi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> geçersiz seri hale getirmeler işlemleri nedeniyle oluşan özel durumları yakalar ve bunları bir içinde kaydırır <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="356a4-107">In .NET 5 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="356a4-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="356a4-108">Version introduced</span></span>

<span data-ttu-id="356a4-109">5.0</span><span class="sxs-lookup"><span data-stu-id="356a4-109">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="356a4-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="356a4-110">Recommended action</span></span>

<span data-ttu-id="356a4-111">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="356a4-111">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="356a4-112">Ancak, çağrı siteniz oluşan belirli bir özel duruma bağlıysa, <xref:System.Runtime.Serialization.SerializationException> Aşağıdaki örnekte gösterildiği gibi, özel durumu dıştaki öğesinden geri sardırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356a4-112">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="356a4-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="356a4-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
