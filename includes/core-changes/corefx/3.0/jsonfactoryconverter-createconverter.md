---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721294"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter. CreateConverter imzası değişti

Sınıfların oluşumunu kolaylaştırmak için <xref:System.Text.Json.Serialization.JsonConverterFactory> , <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> yöntemi genel yapıldı ve türünde ikinci bir bağımsız değişken verildi <xref:System.Text.Json.JsonSerializerOptions> .

#### <a name="change-description"></a>Açıklamayı Değiştir

`CreateConverter`.NET Core sürümündeki 3,0 Preview 8 ' den önceki yöntemin imzası:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

.NET Core 3,0 Preview 8 ve sonraki sürümlerinde, şu şekilde olur:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Bu değişiklikten önce, bunu yapmanın kolay bir yolu olmadığından, korumalı fabrika dönüştürücülerini oluşturmak zordur <xref:System.Text.Json.Serialization.JsonConverter%601> . Fabrika yöntemini herkese açık hale getirme ve ayrıca, <xref:System.Text.Json.JsonSerializerOptions> daha fazla esnek bileşim için geçerli izin vermeyi geçirme.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Türetilmiş sınıfların güncellenmesi ve yeniden derlenmesi gerekiyor.

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
