---
title: Ağ config ayarları
description: .NET Core uygulamaları için ağ yapılandırması yapan çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989109"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="d3bd7-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d3bd7-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="d3bd7-104">HTTP/2 protokolü</span><span class="sxs-lookup"><span data-stu-id="d3bd7-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="d3bd7-105">HTTP/2 protokolü için desteğin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="d3bd7-106">Varsayılan: Devre`false`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="d3bd7-106">Default: Disabled (`false`).</span></span>

- <span data-ttu-id="d3bd7-107">.NET Core 3.0 ile tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="d3bd7-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="d3bd7-108">Setting name</span></span> | <span data-ttu-id="d3bd7-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="d3bd7-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d3bd7-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="d3bd7-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="d3bd7-111">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="d3bd7-111">`false` - disabled</span></span><br/><span data-ttu-id="d3bd7-112">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="d3bd7-112">`true` - enabled</span></span> |
| <span data-ttu-id="d3bd7-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="d3bd7-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="d3bd7-114">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="d3bd7-114">`0` - disabled</span></span><br/><span data-ttu-id="d3bd7-115">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="d3bd7-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="d3bd7-116">Kullanım SoketiHttpHandler</span><span class="sxs-lookup"><span data-stu-id="d3bd7-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="d3bd7-117"><xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> Kullanır <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya eski HTTP protokol yığınları<xref:System.Net.Http.WinHttpHandler> (Windows `CurlHandler`ve , [libcurl](https://curl.haxx.se/libcurl/)üstüne uygulanan bir iç sınıf , Linux üzerinde) yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-117">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="d3bd7-118"><xref:System.Net.Http.HttpClientHandler> Sınıfı doğrudan anında kullanmak yerine üst düzey ağ API'leri kullanıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-118">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="d3bd7-119">Bu ayar, http iletişim kuralı yığınının, httpclientFactory <xref:System.Net.Http.HttpClient> ve [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118))dahil olmak üzere üst düzey ağ API'leri tarafından kullanıldığını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-119">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="d3bd7-120">Varsayılan: <xref:System.Net.Http.SocketsHttpHandler> Kullanım`true`( ).</span><span class="sxs-lookup"><span data-stu-id="d3bd7-120">Default: Use <xref:System.Net.Http.SocketsHttpHandler> (`true`).</span></span>

- <span data-ttu-id="d3bd7-121">Yöntemi çağırarak <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> bu ayarı programlı olarak yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-121">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="d3bd7-122">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="d3bd7-122">Setting name</span></span> | <span data-ttu-id="d3bd7-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="d3bd7-123">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d3bd7-124">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="d3bd7-124">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="d3bd7-125">`true`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="d3bd7-125">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="d3bd7-126">`false`- <xref:System.Net.Http.WinHttpHandler> Linux'ta Windows veya [libcurl](https://curl.haxx.se/libcurl/) kullanımı sağlar</span><span class="sxs-lookup"><span data-stu-id="d3bd7-126">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="d3bd7-127">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="d3bd7-127">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="d3bd7-128">`1`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="d3bd7-128">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="d3bd7-129">`0`- <xref:System.Net.Http.WinHttpHandler> Linux'ta Windows veya [libcurl](https://curl.haxx.se/libcurl/) kullanımı sağlar</span><span class="sxs-lookup"><span data-stu-id="d3bd7-129">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="d3bd7-130">.NET 5'ten `System.Net.Http.UseSocketsHttpHandler` başlayarak, ayar artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d3bd7-130">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
