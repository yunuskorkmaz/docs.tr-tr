---
title: Ağ yapılandırması ayarları
description: .NET Core uygulamaları için ağı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6b5e03b127f95911b712b66c0be8a4f5a2929fc2
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761947"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="529ea-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="529ea-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="529ea-104">HTTP/2 Protokolü</span><span class="sxs-lookup"><span data-stu-id="529ea-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="529ea-105">HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="529ea-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="529ea-106">Bu ayarı atlarsanız, HTTP/2 protokolü desteği devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="529ea-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="529ea-107">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="529ea-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="529ea-108">.NET Core 3,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="529ea-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="529ea-109">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="529ea-109">Setting name</span></span> | <span data-ttu-id="529ea-110">Değerler</span><span class="sxs-lookup"><span data-stu-id="529ea-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="529ea-111">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="529ea-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="529ea-112">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="529ea-112">`false` - disabled</span></span><br/><span data-ttu-id="529ea-113">`true`-etkin</span><span class="sxs-lookup"><span data-stu-id="529ea-113">`true` - enabled</span></span> |
| <span data-ttu-id="529ea-114">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="529ea-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="529ea-115">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="529ea-115">`0` - disabled</span></span><br/><span data-ttu-id="529ea-116">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="529ea-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="529ea-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="529ea-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="529ea-118"><xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>Kullanımlar <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya daha eski http protokol yığınları ( <xref:System.Net.Http.WinHttpHandler> Windows 'Da ve `CurlHandler` , Linux üzerinde [libkıvlıya](https://curl.haxx.se/libcurl/)uygulanan bir iç sınıf) olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="529ea-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="529ea-119">Sınıfı doğrudan başlatmak yerine yüksek düzey ağ API 'Leri kullanıyor olabilirsiniz <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="529ea-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="529ea-120">Bu ayar ayrıca, <xref:System.Net.Http.HttpClient> ve [Httpclientfactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118))dahil olmak üzere üst düzey ağ API 'LERI tarafından kullanılan http Protokolü yığınını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="529ea-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="529ea-121">Bu ayarı atlarsanız, <xref:System.Net.Http.HttpClientHandler> kullanır <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="529ea-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="529ea-122">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="529ea-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="529ea-123">Yöntemini çağırarak bu ayarı programlı bir şekilde yapılandırabilirsiniz <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="529ea-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="529ea-124">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="529ea-124">Setting name</span></span> | <span data-ttu-id="529ea-125">Değerler</span><span class="sxs-lookup"><span data-stu-id="529ea-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="529ea-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="529ea-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="529ea-127">`true`-öğesinin kullanımını etkinleştirilir<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="529ea-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="529ea-128">`false`- <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün</span><span class="sxs-lookup"><span data-stu-id="529ea-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="529ea-129">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="529ea-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="529ea-130">`1`-öğesinin kullanımını etkinleştirilir<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="529ea-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="529ea-131">`0`- <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün</span><span class="sxs-lookup"><span data-stu-id="529ea-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="529ea-132">.NET 5 ' den başlayarak, `System.Net.Http.UseSocketsHttpHandler` ayar artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="529ea-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
