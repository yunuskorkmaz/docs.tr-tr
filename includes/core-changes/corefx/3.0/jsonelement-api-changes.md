---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568075"
---
### <a name="jsonelement-api-changes"></a>JsonElement API değişiklikleri

.NET Core 3,0 Preview 7 ' den itibaren, bazı <xref:System.Text.Json.JsonElement> API 'Leri daha kolay bulma ve daha fazla kullanılabilirlik için izin verecek şekilde değiştirilmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 7 ' de, daha kolay bulma ve daha fazla kullanılabilirlik sağlamak için <xref:System.Text.Json.JsonElement> API 'Leri aşağıdaki şekilde değiştirilmiştir.

1. Tüm `WriteProperty` yöntemi aşırı yüklemeleri <xref:System.Text.Json.JsonElement>kaldırıldı. Bu, aşağıdaki gibi kodu etkiler:

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

1. `WriteValue` <xref:System.Text.Json.JsonElement.WriteTo%2A>olarak yeniden adlandırıldı. Bu, aşağıdaki gibi kodu etkiler:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> artık yöntem parametresi `null`olduğunda bir <xref:System.ArgumentNullException> oluşturur.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 7

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz bu değişikliklerden etkileniyorsa, şunları yapabilirsiniz:

- <xref:System.Text.Json.JsonElement>`WriteProperty` aşırı yüklemeler için bir değiştirme API 'si yoktur. Bunun yerine, aynı sonuca ulaşmak için <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemi ile birlikte <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> aşırı yüklerden birini çağırabilirsiniz. Örneğin:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- `WriteValue` yöntemini <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>olarak yeniden adlandırın. Yöntem parametresi değişmeden kalır. Örneğin, önceki kodun aşağıdaki şekilde değiştirilmesi gerekir:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemine yapılan çağrılarındaki <xref:System.ArgumentNullException> işleyin.

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
