---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568075"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="cc76d-101">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="cc76d-101">JsonElement API changes</span></span>

<span data-ttu-id="cc76d-102">.NET Core 3.0 Preview 7 <xref:System.Text.Json.JsonElement> ile başlayarak, bazı API'ler daha kolay keşfe ve daha fazla kullanılabilirliğe olanak sağlayacak şekilde değişti.</span><span class="sxs-lookup"><span data-stu-id="cc76d-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cc76d-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="cc76d-103">Change description</span></span>

<span data-ttu-id="cc76d-104">.NET Core 3.0 Preview <xref:System.Text.Json.JsonElement> 7'de, API'ler daha kolay keşfe ve daha fazla kullanılabilirliğe olanak sağlamak için aşağıdaki gibi değişti.</span><span class="sxs-lookup"><span data-stu-id="cc76d-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="cc76d-105">Tüm `WriteProperty` yöntem aşırı yükleri <xref:System.Text.Json.JsonElement>kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="cc76d-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="cc76d-106">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="cc76d-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="cc76d-107">`WriteValue`olarak yeniden <xref:System.Text.Json.JsonElement.WriteTo%2A>adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="cc76d-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="cc76d-108">Bu, aşağıdaki gibi kodu etkiler:</span><span class="sxs-lookup"><span data-stu-id="cc76d-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="cc76d-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>şimdi yöntem <xref:System.ArgumentNullException> parametresi olduğunda `null`bir atar.</span><span class="sxs-lookup"><span data-stu-id="cc76d-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cc76d-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="cc76d-110">Version introduced</span></span>

<span data-ttu-id="cc76d-111">3.0 Önizleme 7</span><span class="sxs-lookup"><span data-stu-id="cc76d-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cc76d-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cc76d-112">Recommended action</span></span>

<span data-ttu-id="cc76d-113">Kodunuz bu değişikliklerden etkileniyorsa, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cc76d-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="cc76d-114">'deki aşırı yüklemeler `WriteProperty` için yedek <xref:System.Text.Json.JsonElement>API yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc76d-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="cc76d-115">Bunun yerine, aynı sonucu <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> elde etmek <xref:System.Text.Json.JsonElement.WriteTo%2A> için yöntemle birlikte aşırı yüklerden birini arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc76d-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="cc76d-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="cc76d-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="cc76d-117">Yöntemi ' `WriteValue` ye <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cc76d-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="cc76d-118">Yöntem parametresi değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="cc76d-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="cc76d-119">Örneğin, önceki kod aşağıdaki gibi değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="cc76d-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="cc76d-120"><xref:System.Text.Json.JsonElement.WriteTo%2A> Yönteme <xref:System.ArgumentNullException> yapılan çağrıları ele alın.</span><span class="sxs-lookup"><span data-stu-id="cc76d-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cc76d-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cc76d-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
