---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930063"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter. CreateConverter imzası değişti

<xref:System.Text.Json.Serialization.JsonConverterFactory> Sınıfların oluşumunu kolaylaştırmak için <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> , yöntemi genel yapıldı ve türünde <xref:System.Text.Json.JsonSerializerOptions>ikinci bir bağımsız değişken verildi.

#### <a name="details"></a>Ayrıntılar

.NET Core sürümündeki 3,0 `CreateConverter` Preview 8 ' den önceki yöntemin imzası: 

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

Bu değişiklikten önce, bunu yapmanın kolay bir yolu <xref:System.Text.Json.Serialization.JsonConverter%601> olmadığından, korumalı fabrika dönüştürücülerini oluşturmak zordur. Fabrika yöntemini herkese açık hale getirme ve ayrıca, daha <xref:System.Text.Json.JsonSerializerOptions> fazla esnek bileşim için geçerli izin vermeyi geçirme.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Türetilmiş sınıfların güncellenmesi ve yeniden derlenmesi gerekiyor.

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
