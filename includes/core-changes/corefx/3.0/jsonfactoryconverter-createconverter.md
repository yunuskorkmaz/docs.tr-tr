---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721294"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="24da1-101">JsonFactoryConverter. CreateConverter imzası değişti</span><span class="sxs-lookup"><span data-stu-id="24da1-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="24da1-102">Sınıfların oluşumunu kolaylaştırmak için <xref:System.Text.Json.Serialization.JsonConverterFactory> , <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> yöntemi genel yapıldı ve türünde ikinci bir bağımsız değişken verildi <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="24da1-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="24da1-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="24da1-103">Change description</span></span>

<span data-ttu-id="24da1-104">`CreateConverter`.NET Core sürümündeki 3,0 Preview 8 ' den önceki yöntemin imzası:</span><span class="sxs-lookup"><span data-stu-id="24da1-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="24da1-105">.NET Core 3,0 Preview 8 ve sonraki sürümlerinde, şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="24da1-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="24da1-106">Bu değişiklikten önce, bunu yapmanın kolay bir yolu olmadığından, korumalı fabrika dönüştürücülerini oluşturmak zordur <xref:System.Text.Json.Serialization.JsonConverter%601> .</span><span class="sxs-lookup"><span data-stu-id="24da1-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="24da1-107">Fabrika yöntemini herkese açık hale getirme ve ayrıca, <xref:System.Text.Json.JsonSerializerOptions> daha fazla esnek bileşim için geçerli izin vermeyi geçirme.</span><span class="sxs-lookup"><span data-stu-id="24da1-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24da1-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="24da1-108">Version introduced</span></span>

<span data-ttu-id="24da1-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="24da1-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24da1-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="24da1-110">Recommended action</span></span>

<span data-ttu-id="24da1-111">Türetilmiş sınıfların güncellenmesi ve yeniden derlenmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="24da1-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24da1-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="24da1-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
