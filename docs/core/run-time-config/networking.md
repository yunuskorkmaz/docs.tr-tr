---
title: Ağ yapılandırması ayarları
description: .NET Core uygulamaları için ağı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: d43b68206cc82f4a41df02bd5998702b4f5d0590
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538139"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="b124f-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b124f-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="b124f-104">HTTP/2 Protokolü</span><span class="sxs-lookup"><span data-stu-id="b124f-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="b124f-105">HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b124f-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="b124f-106">Bu ayarı atlarsanız, HTTP/2 protokolü desteği devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b124f-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="b124f-107">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="b124f-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="b124f-108">.NET Core 3,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b124f-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="b124f-109">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="b124f-109">Setting name</span></span> | <span data-ttu-id="b124f-110">Değerler</span><span class="sxs-lookup"><span data-stu-id="b124f-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b124f-111">\*\* Üzerinderuntimeconfig.js\*\*</span><span class="sxs-lookup"><span data-stu-id="b124f-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="b124f-112">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="b124f-112">`false` - disabled</span></span><br/><span data-ttu-id="b124f-113">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="b124f-113">`true` - enabled</span></span> |
| <span data-ttu-id="b124f-114">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="b124f-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="b124f-115">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="b124f-115">`0` - disabled</span></span><br/><span data-ttu-id="b124f-116">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="b124f-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="b124f-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="b124f-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="b124f-118"><xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>Kullanımlar <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya daha eski http protokol yığınları ( <xref:System.Net.Http.WinHttpHandler> Windows 'Da ve `CurlHandler` , Linux üzerinde [libkıvlıya](https://curl.haxx.se/libcurl/)uygulanan bir iç sınıf) olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b124f-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="b124f-119">Sınıfı doğrudan başlatmak yerine yüksek düzey ağ API 'Leri kullanıyor olabilirsiniz <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="b124f-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="b124f-120">Bu ayar ayrıca, <xref:System.Net.Http.HttpClient> ve [Httpclientfactory](/previous-versions/aspnet/hh995280(v=vs.118))dahil olmak üzere üst düzey ağ API 'LERI tarafından kullanılan http Protokolü yığınını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="b124f-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="b124f-121">Bu ayarı atlarsanız, <xref:System.Net.Http.HttpClientHandler> kullanır <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="b124f-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="b124f-122">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="b124f-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="b124f-123">Yöntemini çağırarak bu ayarı programlı bir şekilde yapılandırabilirsiniz <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b124f-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="b124f-124">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="b124f-124">Setting name</span></span> | <span data-ttu-id="b124f-125">Değerler</span><span class="sxs-lookup"><span data-stu-id="b124f-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b124f-126">\*\* Üzerinderuntimeconfig.js\*\*</span><span class="sxs-lookup"><span data-stu-id="b124f-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="b124f-127">`true` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="b124f-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="b124f-128">`false` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün</span><span class="sxs-lookup"><span data-stu-id="b124f-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="b124f-129">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="b124f-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="b124f-130">`1` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="b124f-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="b124f-131">`0` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün</span><span class="sxs-lookup"><span data-stu-id="b124f-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="b124f-132">.NET 5 ' den başlayarak, `System.Net.Http.UseSocketsHttpHandler` ayar artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b124f-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
