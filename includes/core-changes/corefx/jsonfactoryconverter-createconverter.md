---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237484"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter. CreateConverter imzası değişti

@No__t-0 sınıflarının birleşimini kolaylaştırmak için, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> yöntemi genel hale getirilir ve <xref:System.Text.Json.JsonSerializerOptions> türünde ikinci bir bağımsız değişken verildi.

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

Bu değişiklikten önce, <xref:System.Text.Json.Serialization.JsonConverter%601> ' ı almanın kolay bir yolu olmadığından, korumalı fabrika dönüştürücüleri oluşturmak zordur. Fabrika yöntemini ortak hale getirme ve aynı zamanda geçerli <xref:System.Text.Json.JsonSerializerOptions> ' y i daha esnek bir bileşim sağlamak.

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
