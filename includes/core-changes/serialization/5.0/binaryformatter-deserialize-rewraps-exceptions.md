---
ms.openlocfilehash: 2e9267b35c9389da017927aca2346190348265c9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87919328"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="dbbbf-101">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="dbbbf-101">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="dbbbf-102"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Yöntemi artık <xref:System.Runtime.Serialization.SerializationException> özel durumu çağırana geri yaymadan önce bir içindeki bazı özel durum nesnelerini yeniden sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="dbbbf-102">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dbbbf-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="dbbbf-103">Change description</span></span>

<span data-ttu-id="dbbbf-104">Daha önce, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> yöntemi gibi bazı rastgele özel durumlara izin veriliyordu <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="dbbbf-104">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="dbbbf-105">.NET 5,0 ve sonraki sürümlerde yöntemi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> geçersiz seri hale getirmeler işlemleri nedeniyle oluşan özel durumları yakalar ve bunları bir içinde kaydırır <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="dbbbf-105">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dbbbf-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="dbbbf-106">Version introduced</span></span>

<span data-ttu-id="dbbbf-107">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="dbbbf-107">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dbbbf-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="dbbbf-108">Recommended action</span></span>

<span data-ttu-id="dbbbf-109">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dbbbf-109">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="dbbbf-110">Ancak, çağrı siteniz oluşan belirli bir özel duruma bağlıysa, <xref:System.Runtime.Serialization.SerializationException> Aşağıdaki örnekte gösterildiği gibi, özel durumu dıştaki öğesinden geri sardırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbbbf-110">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

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

#### <a name="category"></a><span data-ttu-id="dbbbf-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="dbbbf-111">Category</span></span>

<span data-ttu-id="dbbbf-112">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="dbbbf-112">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dbbbf-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="dbbbf-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
