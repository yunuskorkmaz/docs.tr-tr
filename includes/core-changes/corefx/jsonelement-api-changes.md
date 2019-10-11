---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237486"
---
### <a name="jsonelement-api-changes"></a>JsonElement API değişiklikleri

.NET Core 3,0 Preview 7 ' den itibaren, bazı <xref:System.Text.Json.JsonElement> API 'Leri daha kolay bulma ve daha fazla kullanılabilirlik için izin verecek şekilde değiştirilmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 7 ' de, <xref:System.Text.Json.JsonElement> API 'Leri daha kolay bulma ve daha fazla kullanılabilirlik sağlamak için aşağıdaki şekilde değiştirilmiştir.

1. Tüm `WriteProperty` yöntem aşırı yüklemeleri <xref:System.Text.Json.JsonElement> ' den kaldırıldı. Bu, aşağıdaki gibi kodu etkiler:

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

1. `WriteValue` <xref:System.Text.Json.JsonElement.WriteTo%2A> olarak yeniden adlandırıldı. Bu, aşağıdaki gibi kodu etkiler:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> artık yöntem parametresi `null` olduğunda bir <xref:System.ArgumentNullException> oluşturur.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 7

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz bu değişikliklerden etkileniyorsa, şunları yapabilirsiniz:

- @No__t-1 ' de `WriteProperty` aşırı yüklemeleri için bir değiştirme API 'SI yoktur. Bunun yerine, aynı sonucu Achive için <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> aşırı yüklerden birini <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemiyle birlikte çağırabilirsiniz. Örneğin:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- @No__t-0 yöntemini <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)> olarak yeniden adlandırın. Yöntem parametresi değişmeden kalır. Örneğin, önceki kodun aşağıdaki şekilde değiştirilmesi gerekir:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- @No__t-1 yöntemine yapılan çağrılarında <xref:System.ArgumentNullException> işleyin.

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
