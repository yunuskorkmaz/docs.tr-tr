---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568075"
---
### <a name="jsonelement-api-changes"></a>JsonElement API değişiklikleri

.NET Core 3.0 Preview 7 <xref:System.Text.Json.JsonElement> ile başlayarak, bazı API'ler daha kolay keşfe ve daha fazla kullanılabilirliğe olanak sağlayacak şekilde değişti.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview <xref:System.Text.Json.JsonElement> 7'de, API'ler daha kolay keşfe ve daha fazla kullanılabilirliğe olanak sağlamak için aşağıdaki gibi değişti.

1. Tüm `WriteProperty` yöntem aşırı yükleri <xref:System.Text.Json.JsonElement>kaldırıldı. Bu, aşağıdaki gibi kodu etkiler:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. `WriteValue`olarak yeniden <xref:System.Text.Json.JsonElement.WriteTo%2A>adlandırıldı. Bu, aşağıdaki gibi kodu etkiler:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>şimdi yöntem <xref:System.ArgumentNullException> parametresi olduğunda `null`bir atar.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 7

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz bu değişikliklerden etkileniyorsa, aşağıdakileri yapabilirsiniz:

- 'deki aşırı yüklemeler `WriteProperty` için yedek <xref:System.Text.Json.JsonElement>API yoktur. Bunun yerine, aynı sonucu <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> elde etmek <xref:System.Text.Json.JsonElement.WriteTo%2A> için yöntemle birlikte aşırı yüklerden birini arayabilirsiniz. Örnek:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Yöntemi ' `WriteValue` ye <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>yeniden adlandırın. Yöntem parametresi değişmeden kalır. Örneğin, önceki kod aşağıdaki gibi değiştirilmelidir:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <xref:System.Text.Json.JsonElement.WriteTo%2A> Yönteme <xref:System.ArgumentNullException> yapılan çağrıları ele alın.

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
