---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147568"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="f273c-101">JsonFactoryConverter.CreateConverter imzası değiştirildi</span><span class="sxs-lookup"><span data-stu-id="f273c-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="f273c-102">Sınıfların <xref:System.Text.Json.Serialization.JsonConverterFactory> bileşimini kolaylaştırmak <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> için, yöntem genel kullanıma açıklanmış <xref:System.Text.Json.JsonSerializerOptions>ve ikinci bir tür bağımsız değişkeni verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f273c-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f273c-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f273c-103">Change description</span></span>

<span data-ttu-id="f273c-104">3.0 `CreateConverter` Önizleme 8 sürümünden önce .NET Core'daki yöntemin imzası:</span><span class="sxs-lookup"><span data-stu-id="f273c-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="f273c-105">.NET Core 3.0 Önizleme 8 ve sonraki sürümlerinde, şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f273c-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="f273c-106">Bu değişiklikten önce, mühürlü fabrika dönüştürücüleri oluşturmak zordu, çünkü ondan <xref:System.Text.Json.Serialization.JsonConverter%601> almak için kolay bir yol yoktu.</span><span class="sxs-lookup"><span data-stu-id="f273c-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="f273c-107">Fabrika yöntemini kamuya alenen <xref:System.Text.Json.JsonSerializerOptions> yapmak ve aynı zamanda mevcut geçen çok daha esnek kompozisyon için izin verir.</span><span class="sxs-lookup"><span data-stu-id="f273c-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f273c-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f273c-108">Version introduced</span></span>

<span data-ttu-id="f273c-109">3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="f273c-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f273c-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f273c-110">Recommended action</span></span>

<span data-ttu-id="f273c-111">Türemiş sınıfların güncelleştirilip yeniden derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f273c-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f273c-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f273c-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
