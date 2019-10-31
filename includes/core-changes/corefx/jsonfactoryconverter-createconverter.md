---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198586"
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

Bu değişiklikten önce, bundan <xref:System.Text.Json.Serialization.JsonConverter%601> almanın kolay bir yolu olmadığından, korumalı fabrika dönüştürücülerini oluşturmak zordur. Fabrika yöntemini ortak hale getirme ve aynı zamanda geçerli <xref:System.Text.Json.JsonSerializerOptions> ' y i daha esnek bir bileşim sağlamak.

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
