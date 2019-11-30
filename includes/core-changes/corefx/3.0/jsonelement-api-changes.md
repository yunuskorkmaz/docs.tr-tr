---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568075"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="3e059-101">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3e059-101">JsonElement API changes</span></span>

<span data-ttu-id="3e059-102">.NET Core 3,0 Preview 7 ' den itibaren, bazı <xref:System.Text.Json.JsonElement> API 'Leri daha kolay bulma ve daha fazla kullanılabilirlik için izin verecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e059-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3e059-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3e059-103">Change description</span></span>

<span data-ttu-id="3e059-104">.NET Core 3,0 Preview 7 ' de, daha kolay bulma ve daha fazla kullanılabilirlik sağlamak için <xref:System.Text.Json.JsonElement> API 'Leri aşağıdaki şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e059-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="3e059-105">Tüm `WriteProperty` yöntemi aşırı yüklemeleri <xref:System.Text.Json.JsonElement>kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="3e059-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="3e059-106">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="3e059-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="3e059-107">`WriteValue` <xref:System.Text.Json.JsonElement.WriteTo%2A>olarak yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="3e059-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="3e059-108">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="3e059-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="3e059-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> artık yöntem parametresi `null`olduğunda bir <xref:System.ArgumentNullException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e059-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3e059-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3e059-110">Version introduced</span></span>

<span data-ttu-id="3e059-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="3e059-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3e059-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3e059-112">Recommended action</span></span>

<span data-ttu-id="3e059-113">Kodunuz bu değişikliklerden etkileniyorsa, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e059-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="3e059-114"><xref:System.Text.Json.JsonElement>`WriteProperty` aşırı yüklemeler için bir değiştirme API 'si yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e059-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="3e059-115">Bunun yerine, aynı sonuca ulaşmak için <xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemi ile birlikte <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> aşırı yüklerden birini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e059-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="3e059-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3e059-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="3e059-117">`WriteValue` yöntemini <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="3e059-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="3e059-118">Yöntem parametresi değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="3e059-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="3e059-119">Örneğin, önceki kodun aşağıdaki şekilde değiştirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="3e059-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="3e059-120"><xref:System.Text.Json.JsonElement.WriteTo%2A> yöntemine yapılan çağrılarındaki <xref:System.ArgumentNullException> işleyin.</span><span class="sxs-lookup"><span data-stu-id="3e059-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3e059-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3e059-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
