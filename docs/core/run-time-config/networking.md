---
title: Ağ yapılandırması ayarları
description: .NET Core uygulamaları için ağı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188308"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="09235-103">Ağ için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="09235-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="09235-104">HTTP/2 Protokolü</span><span class="sxs-lookup"><span data-stu-id="09235-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="09235-105">HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="09235-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="09235-106">.NET Core 3,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="09235-106">Introduced in .NET Core 3.0.</span></span>

- <span data-ttu-id="09235-107">Yalnızca .NET Core 3,0: Bu ayarı atlarsanız, HTTP/2 protokolü desteği devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="09235-107">.NET Core 3.0 only: If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="09235-108">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="09235-108">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="09235-109">.NET Core 3,1 ve .NET 5 +: Bu ayarı atlarsanız, HTTP/2 Protokolü için destek etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="09235-109">.NET Core 3.1 and .NET 5+: If you omit this setting, support for the HTTP/2 protocol is enabled.</span></span> <span data-ttu-id="09235-110">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="09235-110">This is equivalent to setting the value to `true`.</span></span>

| | <span data-ttu-id="09235-111">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="09235-111">Setting name</span></span> | <span data-ttu-id="09235-112">Değerler</span><span class="sxs-lookup"><span data-stu-id="09235-112">Values</span></span> |
| - | - | - |
| <span data-ttu-id="09235-113">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="09235-113">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="09235-114">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="09235-114">`false` - disabled</span></span><br/><span data-ttu-id="09235-115">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="09235-115">`true` - enabled</span></span> |
| <span data-ttu-id="09235-116">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="09235-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="09235-117">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="09235-117">`0` - disabled</span></span><br/><span data-ttu-id="09235-118">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="09235-118">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="09235-119">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="09235-119">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="09235-120"><xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>Kullanımlar <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya daha eski http protokol yığınları ( <xref:System.Net.Http.WinHttpHandler> Windows 'Da ve `CurlHandler` , Linux üzerinde [libkıvlıya](https://curl.haxx.se/libcurl/)uygulanan bir iç sınıf) olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="09235-120">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="09235-121">Sınıfı doğrudan başlatmak yerine yüksek düzey ağ API 'Leri kullanıyor olabilirsiniz <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="09235-121">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="09235-122">Bu ayar ayrıca, <xref:System.Net.Http.HttpClient> ve [Httpclientfactory](/previous-versions/aspnet/hh995280(v=vs.118))dahil olmak üzere üst düzey ağ API 'LERI tarafından kullanılan http Protokolü yığınını da etkiler.</span><span class="sxs-lookup"><span data-stu-id="09235-122">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="09235-123">Bu ayarı atlarsanız, <xref:System.Net.Http.HttpClientHandler> kullanır <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="09235-123">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="09235-124">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="09235-124">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="09235-125">Yöntemini çağırarak bu ayarı programlı bir şekilde yapılandırabilirsiniz <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="09235-125">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="09235-126">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="09235-126">Setting name</span></span> | <span data-ttu-id="09235-127">Değerler</span><span class="sxs-lookup"><span data-stu-id="09235-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="09235-128">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="09235-128">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="09235-129">`true` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="09235-129">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="09235-130">`false` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün</span><span class="sxs-lookup"><span data-stu-id="09235-130">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="09235-131">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="09235-131">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="09235-132">`1` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="09235-132">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="09235-133">`0` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün</span><span class="sxs-lookup"><span data-stu-id="09235-133">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="09235-134">.NET 5 ' den başlayarak, `System.Net.Http.UseSocketsHttpHandler` ayar artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="09235-134">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>

## <a name="latin1-headers-net-core-31-only"></a><span data-ttu-id="09235-135">Latin1 üstbilgileri (yalnızca .NET Core 3,1)</span><span class="sxs-lookup"><span data-stu-id="09235-135">Latin1 headers (.NET Core 3.1 only)</span></span>

- <span data-ttu-id="09235-136">Bu anahtar, <xref:System.Net.Http.SocketsHttpHandler> üst BILGIDE ISO-8859-1 (Latin-1) kodlu karakter gönderilmesini sağlayan http üst bilgi doğrulamasını yeniden sağlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="09235-136">This switch allows relaxing the HTTP header validation, enabling <xref:System.Net.Http.SocketsHttpHandler> to send ISO-8859-1 (Latin-1) encoded characters in headers.</span></span>

- <span data-ttu-id="09235-137">Bu ayarı atlarsanız, ASCII olmayan bir karakter gönderme girişimi buna neden olur <xref:System.Net.Http.HttpRequestException> .</span><span class="sxs-lookup"><span data-stu-id="09235-137">If you omit this setting, an attempt to send a non-ASCII character will result in <xref:System.Net.Http.HttpRequestException>.</span></span> <span data-ttu-id="09235-138">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="09235-138">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="09235-139">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="09235-139">Setting name</span></span> | <span data-ttu-id="09235-140">Değerler</span><span class="sxs-lookup"><span data-stu-id="09235-140">Values</span></span> |
| - | - | - |
| <span data-ttu-id="09235-141">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="09235-141">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | <span data-ttu-id="09235-142">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="09235-142">`false` - disabled</span></span><br/><span data-ttu-id="09235-143">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="09235-143">`true` - enabled</span></span> |
| <span data-ttu-id="09235-144">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="09235-144">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | <span data-ttu-id="09235-145">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="09235-145">`0` - disabled</span></span><br/><span data-ttu-id="09235-146">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="09235-146">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="09235-147">Bu seçenek, önceki veya sonraki sürümlerde değil, .NET Core 3,1 sürümünde 3.1.9 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09235-147">This option is only available in .NET Core 3.1 since version 3.1.9, and not in previous or later versions.</span></span> <span data-ttu-id="09235-148">.NET 5 ' te kullanmanızı öneririz <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> .</span><span class="sxs-lookup"><span data-stu-id="09235-148">In .NET 5 we recommend using <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector>.</span></span>
