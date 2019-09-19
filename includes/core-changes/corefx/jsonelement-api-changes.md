---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119305"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="39059-101">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="39059-101">JsonElement API changes</span></span>

<span data-ttu-id="39059-102">.NET Core 3,0 Preview 7 ' den itibaren, <xref:System.Text.Json.JsonElement> bazı API 'ler daha kolay bulma ve daha fazla kullanılabilirlik için izin verecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="39059-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="39059-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="39059-103">Change description</span></span>

<span data-ttu-id="39059-104">.NET Core 3,0 Preview 7 ' de <xref:System.Text.Json.JsonElement> , API 'ler daha kolay bulma ve daha fazla kullanılabilirlik sağlamak için aşağıdaki şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="39059-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="39059-105">Tüm `WriteProperty` yöntem aşırı yüklemeleri öğesinden <xref:System.Text.Json.JsonElement>kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="39059-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="39059-106">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="39059-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="39059-107">`WriteValue`, olarak <xref:System.Text.Json.JsonElement.WriteTo%2A>yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="39059-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="39059-108">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="39059-108">This affects code such as the following:</span></span>

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <span data-ttu-id="39059-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>Şimdi, <xref:System.ArgumentNullException> `null`yöntemi parametresi olduğunda bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39059-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39059-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="39059-110">Version introduced</span></span>

<span data-ttu-id="39059-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="39059-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39059-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="39059-112">Recommended action</span></span>

<span data-ttu-id="39059-113">Kodunuz bu değişikliklerden etkileniyorsa, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="39059-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="39059-114">`WriteProperty` İçindeki<xref:System.Text.Json.JsonElement>aşırı yüklemeler için bir değiştirme API 'si yoktur.</span><span class="sxs-lookup"><span data-stu-id="39059-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="39059-115">Bunun yerine, <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> aşırı yüklerden birini, aynı sonucu Achive için <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemiyle birlikte çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39059-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="39059-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="39059-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="39059-117">`WriteValue` Yöntemini olarak<xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="39059-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="39059-118">Yöntem parametresi değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="39059-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="39059-119">Örneğin, önceki kodun aşağıdaki şekilde değiştirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="39059-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="39059-120">Yöntemineyapılan<xref:System.Text.Json.JsonElement.WriteTo%2A> çağrıları işleyin. <xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="39059-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39059-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="39059-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
