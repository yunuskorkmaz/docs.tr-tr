---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119305"
---
### <a name="jsonelement-api-changes"></a>JsonElement API değişiklikleri

.NET Core 3,0 Preview 7 ' den itibaren, <xref:System.Text.Json.JsonElement> bazı API 'ler daha kolay bulma ve daha fazla kullanılabilirlik için izin verecek şekilde değiştirilmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 7 ' de <xref:System.Text.Json.JsonElement> , API 'ler daha kolay bulma ve daha fazla kullanılabilirlik sağlamak için aşağıdaki şekilde değiştirilmiştir.

1. Tüm `WriteProperty` yöntem aşırı yüklemeleri öğesinden <xref:System.Text.Json.JsonElement>kaldırıldı. Bu, aşağıdaki gibi kodu etkiler:

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

1. `WriteValue`, olarak <xref:System.Text.Json.JsonElement.WriteTo%2A>yeniden adlandırıldı. Bu, aşağıdaki gibi kodu etkiler:

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>Şimdi, <xref:System.ArgumentNullException> `null`yöntemi parametresi olduğunda bir oluşturur.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 7

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz bu değişikliklerden etkileniyorsa, şunları yapabilirsiniz:

- `WriteProperty` İçindeki<xref:System.Text.Json.JsonElement>aşırı yüklemeler için bir değiştirme API 'si yoktur. Bunun yerine, <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> aşırı yüklerden birini, aynı sonucu Achive için <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemiyle birlikte çağırabilirsiniz. Örneğin:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- `WriteValue` Yöntemini olarak<xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>yeniden adlandırın. Yöntem parametresi değişmeden kalır. Örneğin, önceki kodun aşağıdaki şekilde değiştirilmesi gerekir:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Yöntemineyapılan<xref:System.Text.Json.JsonElement.WriteTo%2A> çağrıları işleyin. <xref:System.ArgumentNullException>

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
