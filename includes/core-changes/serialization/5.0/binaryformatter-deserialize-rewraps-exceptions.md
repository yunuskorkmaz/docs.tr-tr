---
ms.openlocfilehash: 4aef35502fc93cbf0399e3c8d0932338829d6c07
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517365"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Yöntemi artık <xref:System.Runtime.Serialization.SerializationException> özel durumu çağırana geri yaymadan önce bir içindeki bazı özel durum nesnelerini yeniden sarmalanmış.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> yöntemi gibi bazı rastgele özel durumlara izin veriliyordu <xref:System.ArgumentNullException> .

.NET 5,0 ve sonraki sürümlerde yöntemi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> geçersiz seri hale getirmeler işlemleri nedeniyle oluşan özel durumları yakalar ve bunları bir içinde kaydırır <xref:System.Runtime.Serialization.SerializationException> .

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, herhangi bir işlem yapmanız gerekmez. Ancak, çağrı siteniz oluşan belirli bir özel duruma bağlıysa, <xref:System.Runtime.Serialization.SerializationException> Aşağıdaki örnekte gösterildiği gibi, özel durumu dıştaki öğesinden geri sardırabilirsiniz.

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
catch (SerializationException serEx)
{
    if (serEx.InnerException is MyException myEx)
    {
        // Handle 'myEx' here in case it was wrapped in SerializationException.
    }
    else
    {
        throw;
    }
}
```

#### <a name="category"></a>Kategori

Serileştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
