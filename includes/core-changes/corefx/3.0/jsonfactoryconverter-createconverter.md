---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147568"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter.CreateConverter imzası değiştirildi

Sınıfların <xref:System.Text.Json.Serialization.JsonConverterFactory> bileşimini kolaylaştırmak <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> için, yöntem genel kullanıma açıklanmış <xref:System.Text.Json.JsonSerializerOptions>ve ikinci bir tür bağımsız değişkeni verilmiştir.

#### <a name="change-description"></a>Açıklamayı değiştir

3.0 `CreateConverter` Önizleme 8 sürümünden önce .NET Core'daki yöntemin imzası:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

.NET Core 3.0 Önizleme 8 ve sonraki sürümlerinde, şu şekildedir:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Bu değişiklikten önce, mühürlü fabrika dönüştürücüleri oluşturmak zordu, çünkü ondan <xref:System.Text.Json.Serialization.JsonConverter%601> almak için kolay bir yol yoktu. Fabrika yöntemini kamuya alenen <xref:System.Text.Json.JsonSerializerOptions> yapmak ve aynı zamanda mevcut geçen çok daha esnek kompozisyon için izin verir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 8

#### <a name="recommended-action"></a>Önerilen eylem

Türemiş sınıfların güncelleştirilip yeniden derlenmesi gerekir.

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
