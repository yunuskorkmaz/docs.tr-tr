---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237484"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="c8b61-101">JsonFactoryConverter. CreateConverter imzası değişti</span><span class="sxs-lookup"><span data-stu-id="c8b61-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="c8b61-102">@No__t-0 sınıflarının birleşimini kolaylaştırmak için, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> yöntemi genel hale getirilir ve <xref:System.Text.Json.JsonSerializerOptions> türünde ikinci bir bağımsız değişken verildi.</span><span class="sxs-lookup"><span data-stu-id="c8b61-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c8b61-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c8b61-103">Change description</span></span>

<span data-ttu-id="c8b61-104">.NET Core 'da sürüm 3,0 Preview 8 ' den önceki `CreateConverter` yönteminin imzası:</span><span class="sxs-lookup"><span data-stu-id="c8b61-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="c8b61-105">.NET Core 3,0 Preview 8 ve sonraki sürümlerinde, şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="c8b61-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="c8b61-106">Bu değişiklikten önce, <xref:System.Text.Json.Serialization.JsonConverter%601> ' ı almanın kolay bir yolu olmadığından, korumalı fabrika dönüştürücüleri oluşturmak zordur.</span><span class="sxs-lookup"><span data-stu-id="c8b61-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="c8b61-107">Fabrika yöntemini ortak hale getirme ve aynı zamanda geçerli <xref:System.Text.Json.JsonSerializerOptions> ' y i daha esnek bir bileşim sağlamak.</span><span class="sxs-lookup"><span data-stu-id="c8b61-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c8b61-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c8b61-108">Version introduced</span></span>

<span data-ttu-id="c8b61-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="c8b61-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c8b61-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c8b61-110">Recommended action</span></span>

<span data-ttu-id="c8b61-111">Türetilmiş sınıfların güncellenmesi ve yeniden derlenmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="c8b61-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c8b61-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c8b61-112">Affected APIs</span></span>

<span data-ttu-id="c8b61-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8b61-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
