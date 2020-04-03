---
title: Ağ config ayarları
description: .NET Core uygulamaları için ağ yapılandırması yapan çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: f5ea47f0444a911dc2347a66817cabf585fd8e70
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635421"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="ade8f-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ade8f-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="ade8f-104">HTTP/2 protokolü</span><span class="sxs-lookup"><span data-stu-id="ade8f-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="ade8f-105">HTTP/2 protokolü için desteğin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ade8f-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="ade8f-106">Varsayılan: Devre`false`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="ade8f-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="ade8f-107">.NET Core 3.0 ile tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="ade8f-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="ade8f-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="ade8f-108">Setting name</span></span> | <span data-ttu-id="ade8f-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="ade8f-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ade8f-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ade8f-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="ade8f-111">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="ade8f-111">`false` - disabled</span></span><br/><span data-ttu-id="ade8f-112">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="ade8f-112">`true` - enabled</span></span> |
| <span data-ttu-id="ade8f-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="ade8f-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="ade8f-114">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="ade8f-114">`0` - disabled</span></span><br/><span data-ttu-id="ade8f-115">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="ade8f-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="ade8f-116">Kullanım SoketiHttpHandler</span><span class="sxs-lookup"><span data-stu-id="ade8f-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="ade8f-117">[Libcurl'e](https://curl.haxx.se/libcurl/)dayalı, kullanımı <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uygulanması <xref:System.Net.Http.HttpClient>gibi üst düzey ağ API'lerinin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ade8f-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="ade8f-118">Varsayılan: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Kullanım`true`( ).</span><span class="sxs-lookup"><span data-stu-id="ade8f-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="ade8f-119">Yöntemi çağırarak <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> bu ayarı programlı olarak yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ade8f-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="ade8f-120">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="ade8f-120">Setting name</span></span> | <span data-ttu-id="ade8f-121">Değerler</span><span class="sxs-lookup"><span data-stu-id="ade8f-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ade8f-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ade8f-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="ade8f-123">`true`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="ade8f-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="ade8f-124">`false`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="ade8f-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="ade8f-125">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="ade8f-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="ade8f-126">`1`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="ade8f-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="ade8f-127">`0`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="ade8f-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |

> [!NOTE]
> <span data-ttu-id="ade8f-128">.NET 5'ten `System.Net.Http.UseSocketsHttpHandler` başlayarak, ayar artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ade8f-128">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
