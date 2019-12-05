---
title: Ağ yapılandırması ayarları
description: .NET Core uygulamaları için ağı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802773"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="86313-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="86313-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="86313-104">HTTP/2 Protokolü</span><span class="sxs-lookup"><span data-stu-id="86313-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="86313-105">HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="86313-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="86313-106">Varsayılan: devre dışı (`false`).</span><span class="sxs-lookup"><span data-stu-id="86313-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="86313-107">.NET Core 3,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="86313-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="86313-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="86313-108">Setting name</span></span> | <span data-ttu-id="86313-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="86313-109">Values</span></span> |
| - | - |
| <span data-ttu-id="86313-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="86313-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="86313-111">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="86313-111">`false` - disabled</span></span><br/><span data-ttu-id="86313-112">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="86313-112">`true` - enabled</span></span> |
| <span data-ttu-id="86313-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="86313-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="86313-114">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="86313-114">`0` - disabled</span></span><br/><span data-ttu-id="86313-115">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="86313-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="86313-116">Sockets HTTP işleyicisi</span><span class="sxs-lookup"><span data-stu-id="86313-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="86313-117"><xref:System.Net.Http.HttpClient>gibi yüksek düzey ağ API 'Lerinin, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uygulanmasını ve bu nesnelerin [Libon](https://curl.haxx.se/libcurl/)'u temel alarak uygulanmasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="86313-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="86313-118">Varsayılan: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`) kullanın.</span><span class="sxs-lookup"><span data-stu-id="86313-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="86313-119">Bu ayarı, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini çağırarak programlı bir şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86313-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="86313-120">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="86313-120">Setting name</span></span> | <span data-ttu-id="86313-121">Değerler</span><span class="sxs-lookup"><span data-stu-id="86313-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86313-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="86313-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="86313-123">`true`-<xref:System.Net.Http.SocketsHttpHandler> kullanımını etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="86313-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="86313-124">`false`-<xref:System.Net.Http.HttpClientHandler> kullanımını etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="86313-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="86313-125">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="86313-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="86313-126">`1`-<xref:System.Net.Http.SocketsHttpHandler> kullanımını etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="86313-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="86313-127">`0`-<xref:System.Net.Http.HttpClientHandler> kullanımını etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="86313-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
