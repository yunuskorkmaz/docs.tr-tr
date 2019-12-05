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
# <a name="run-time-configuration-options-for-networking"></a>Ağ için çalışma zamanı yapılandırma seçenekleri

## <a name="http2-protocol"></a>HTTP/2 Protokolü

- HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.
- Varsayılan: devre dışı (`false`).
- .NET Core 3,0 ' de kullanıma sunulmuştur.

| | Ayar adı | Değerler |
| - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-devre dışı<br/>`true` etkin |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-devre dışı<br/>`1` etkin |

## <a name="sockets-http-handler"></a>Sockets HTTP işleyicisi

- <xref:System.Net.Http.HttpClient>gibi yüksek düzey ağ API 'Lerinin, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uygulanmasını ve bu nesnelerin [Libon](https://curl.haxx.se/libcurl/)'u temel alarak uygulanmasını yapılandırır.
- Varsayılan: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`) kullanın.
- Bu ayarı, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini çağırarak programlı bir şekilde yapılandırabilirsiniz.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true`-<xref:System.Net.Http.SocketsHttpHandler> kullanımını etkinleştirilir<br/>`false`-<xref:System.Net.Http.HttpClientHandler> kullanımını etkinleştirilir |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`-<xref:System.Net.Http.SocketsHttpHandler> kullanımını etkinleştirilir<br/>`0`-<xref:System.Net.Http.HttpClientHandler> kullanımını etkinleştirilir |
