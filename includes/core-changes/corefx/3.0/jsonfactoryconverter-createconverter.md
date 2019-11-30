---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568155"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter. CreateConverter imzası değişti

<xref:System.Text.Json.Serialization.JsonConverterFactory> sınıflarının kompozisyonunu kolaylaştırmak için, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> yöntemi genel hale getirilir ve <xref:System.Text.Json.JsonSerializerOptions>türünde ikinci bir bağımsız değişken verildi.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 'da sürüm 3,0 Preview 8 ' den önceki `CreateConverter` yönteminin imzası:

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

Bu değişiklikten önce, bundan <xref:System.Text.Json.Serialization.JsonConverter%601> almanın kolay bir yolu olmadığından, korumalı fabrika dönüştürücülerini oluşturmak zordur. Fabrika yöntemini genel hale getirme ve geçerli <xref:System.Text.Json.JsonSerializerOptions> geçirme, çok daha esnek bir bileşim için izin verir.

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
