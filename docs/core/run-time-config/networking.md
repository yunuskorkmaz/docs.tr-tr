---
title: Ağ config ayarları
description: .NET Core uygulamaları için ağ yapılandırması yapan çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802773"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="d63ce-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d63ce-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="d63ce-104">HTTP/2 protokolü</span><span class="sxs-lookup"><span data-stu-id="d63ce-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="d63ce-105">HTTP/2 protokolü için desteğin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d63ce-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="d63ce-106">Varsayılan: Devre`false`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="d63ce-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="d63ce-107">.NET Core 3.0 ile tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="d63ce-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="d63ce-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="d63ce-108">Setting name</span></span> | <span data-ttu-id="d63ce-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="d63ce-109">Values</span></span> |
| - | - |
| <span data-ttu-id="d63ce-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="d63ce-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="d63ce-111">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="d63ce-111">`false` - disabled</span></span><br/><span data-ttu-id="d63ce-112">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="d63ce-112">`true` - enabled</span></span> |
| <span data-ttu-id="d63ce-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="d63ce-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="d63ce-114">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="d63ce-114">`0` - disabled</span></span><br/><span data-ttu-id="d63ce-115">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="d63ce-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="d63ce-116">Soketler HTTP işleyicisi</span><span class="sxs-lookup"><span data-stu-id="d63ce-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="d63ce-117">[Libcurl'e](https://curl.haxx.se/libcurl/)dayalı, kullanımı <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uygulanması <xref:System.Net.Http.HttpClient>gibi üst düzey ağ API'lerinin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d63ce-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="d63ce-118">Varsayılan: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Kullanım`true`( ).</span><span class="sxs-lookup"><span data-stu-id="d63ce-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="d63ce-119">Yöntemi çağırarak <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> bu ayarı programlı olarak yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d63ce-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="d63ce-120">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="d63ce-120">Setting name</span></span> | <span data-ttu-id="d63ce-121">Değerler</span><span class="sxs-lookup"><span data-stu-id="d63ce-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d63ce-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="d63ce-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="d63ce-123">`true`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="d63ce-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="d63ce-124">`false`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="d63ce-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="d63ce-125">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="d63ce-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="d63ce-126">`1`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="d63ce-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="d63ce-127">`0`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="d63ce-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
