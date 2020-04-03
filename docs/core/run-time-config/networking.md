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
# <a name="run-time-configuration-options-for-networking"></a>Ağ için çalışma zamanı yapılandırma seçenekleri

## <a name="http2-protocol"></a>HTTP/2 protokolü

- HTTP/2 protokolü için desteğin etkin olup olmadığını yapılandırır.
- Varsayılan: Devre`false`Dışı ( ).
- .NET Core 3.0 ile tanıtıldı.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- engelli<br/>`true`- etkin |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- engelli<br/>`1`- etkin |

## <a name="usesocketshttphandler"></a>Kullanım SoketiHttpHandler

- [Libcurl'e](https://curl.haxx.se/libcurl/)dayalı, kullanımı <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uygulanması <xref:System.Net.Http.HttpClient>gibi üst düzey ağ API'lerinin olup olmadığını yapılandırır.
- Varsayılan: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Kullanım`true`( ).
- Yöntemi çağırarak <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> bu ayarı programlı olarak yapılandırabilirsiniz.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler> |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- kullanımını sağlar<xref:System.Net.Http.HttpClientHandler> |

> [!NOTE]
> .NET 5'ten `System.Net.Http.UseSocketsHttpHandler` başlayarak, ayar artık kullanılamıyor.
