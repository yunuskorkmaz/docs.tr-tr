---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237486"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="a6daf-101">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a6daf-101">JsonElement API changes</span></span>

<span data-ttu-id="a6daf-102">.NET Core 3,0 Preview 7 ' den itibaren, bazı <xref:System.Text.Json.JsonElement> API 'Leri daha kolay bulma ve daha fazla kullanılabilirlik için izin verecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a6daf-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a6daf-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a6daf-103">Change description</span></span>

<span data-ttu-id="a6daf-104">.NET Core 3,0 Preview 7 ' de, <xref:System.Text.Json.JsonElement> API 'Leri daha kolay bulma ve daha fazla kullanılabilirlik sağlamak için aşağıdaki şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a6daf-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="a6daf-105">Tüm `WriteProperty` yöntem aşırı yüklemeleri <xref:System.Text.Json.JsonElement> ' den kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a6daf-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="a6daf-106">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="a6daf-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="a6daf-107">`WriteValue` <xref:System.Text.Json.JsonElement.WriteTo%2A> olarak yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="a6daf-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="a6daf-108">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="a6daf-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="a6daf-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> artık yöntem parametresi `null` olduğunda bir <xref:System.ArgumentNullException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6daf-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a6daf-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a6daf-110">Version introduced</span></span>

<span data-ttu-id="a6daf-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="a6daf-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a6daf-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a6daf-112">Recommended action</span></span>

<span data-ttu-id="a6daf-113">Kodunuz bu değişikliklerden etkileniyorsa, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a6daf-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="a6daf-114">@No__t-1 ' de `WriteProperty` aşırı yüklemeleri için bir değiştirme API 'SI yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6daf-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="a6daf-115">Bunun yerine, aynı sonucu Achive için <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> aşırı yüklerden birini <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemiyle birlikte çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6daf-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="a6daf-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a6daf-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="a6daf-117">@No__t-0 yöntemini <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)> olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a6daf-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="a6daf-118">Yöntem parametresi değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="a6daf-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="a6daf-119">Örneğin, önceki kodun aşağıdaki şekilde değiştirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="a6daf-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="a6daf-120">@No__t-1 yöntemine yapılan çağrılarında <xref:System.ArgumentNullException> işleyin.</span><span class="sxs-lookup"><span data-stu-id="a6daf-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a6daf-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a6daf-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
