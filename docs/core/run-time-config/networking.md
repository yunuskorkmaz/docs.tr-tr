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
# <a name="run-time-configuration-options-for-networking"></a>Ağ için çalışma zamanı yapılandırma seçenekleri

## <a name="http2-protocol"></a>HTTP/2 protokolü

- HTTP/2 protokolü için desteğin etkin olup olmadığını yapılandırır.
- Varsayılan: Devre`false`Dışı ( ).
- .NET Core 3.0 ile tanıtıldı.

| | Ayar adı | Değerler |
| - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- engelli<br/>`true`- etkin |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- engelli<br/>`1`- etkin |

## <a name="sockets-http-handler"></a>Soketler HTTP işleyicisi

- [Libcurl'e](https://curl.haxx.se/libcurl/)dayalı, kullanımı <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uygulanması <xref:System.Net.Http.HttpClient>gibi üst düzey ağ API'lerinin olup olmadığını yapılandırır.
- Varsayılan: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Kullanım`true`( ).
- Yöntemi çağırarak <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> bu ayarı programlı olarak yapılandırabilirsiniz.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler> |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler> |
