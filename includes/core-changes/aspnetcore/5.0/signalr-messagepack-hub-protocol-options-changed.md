---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507108"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="32939-101">SignalR: MessagePack hub protokol seçenekleri türü değişti</span><span class="sxs-lookup"><span data-stu-id="32939-101">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="32939-102">ASP.NET Core SignalR MessagePack hub protokol seçenekleri türü, öğesinden `IList<MessagePack.IFormatterResolver>` [MessagePack](https://www.nuget.org/packages/MessagePack) kitaplığının `MessagePackSerializerOptions` türüne değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="32939-102">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="32939-103">Bu değişiklik hakkında tartışma için bkz. [DotNet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="32939-103">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32939-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="32939-104">Version introduced</span></span>

<span data-ttu-id="32939-105">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="32939-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="32939-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="32939-106">Old behavior</span></span>

<span data-ttu-id="32939-107">Seçeneklere aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32939-107">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="32939-108">Ve seçenekleri aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="32939-108">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

#### <a name="new-behavior"></a><span data-ttu-id="32939-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="32939-109">New behavior</span></span>

<span data-ttu-id="32939-110">Seçeneklere aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32939-110">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="32939-111">Ve seçenekleri aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="32939-111">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

#### <a name="reason-for-change"></a><span data-ttu-id="32939-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="32939-112">Reason for change</span></span>

<span data-ttu-id="32939-113">Bu değişiklik, [ASPNET/Duyurular # 404](https://github.com/aspnet/Announcements/issues/404)' de duyurulan ileti paketi v2. x ' e taşınmasına yönelik bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="32939-113">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="32939-114">V2. x kitaplığı, kullanımı daha kolay olan bir seçenekler API 'SI ekledi ve daha önce sunulan listesinden `MessagePack.IFormatterResolver` daha fazla özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="32939-114">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32939-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="32939-115">Recommended action</span></span>

<span data-ttu-id="32939-116">Bu son değişiklik, üzerinde <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>değer yapılandıran herkesi etkiler.</span><span class="sxs-lookup"><span data-stu-id="32939-116">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="32939-117">ASP.NET Core SignalR MessagePack hub protokolünü kullanıyorsanız ve seçenekleri değiştiriyorsanız, kullanımınızı yukarıda gösterildiği gibi yeni seçenekler API 'sini kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="32939-117">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

#### <a name="category"></a><span data-ttu-id="32939-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="32939-118">Category</span></span>

<span data-ttu-id="32939-119">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="32939-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32939-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="32939-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
