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
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Yöntemi artık <xref:System.Runtime.Serialization.SerializationException> özel durumu çağırana geri yaymadan önce bir içindeki bazı özel durum nesnelerini yeniden sarmalanmış.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> yöntemi gibi bazı rastgele özel durumlara izin veriliyordu <xref:System.ArgumentNullException> .

.NET 5,0 ve sonraki sürümlerde yöntemi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> geçersiz seri hale getirmeler işlemleri nedeniyle oluşan özel durumları yakalar ve bunları bir içinde kaydırır <xref:System.Runtime.Serialization.SerializationException> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

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
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
