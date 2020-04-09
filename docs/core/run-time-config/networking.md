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

- <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> Kullanır <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya eski HTTP protokol yığınları<xref:System.Net.Http.WinHttpHandler> (Windows `CurlHandler`ve , [libcurl](https://curl.haxx.se/libcurl/)üstüne uygulanan bir iç sınıf , Linux üzerinde) yapılandırır.

  > [!NOTE]
  > <xref:System.Net.Http.HttpClientHandler> Sınıfı doğrudan anında kullanmak yerine üst düzey ağ API'leri kullanıyor olabilirsiniz. Bu ayar, http iletişim kuralı yığınının, httpclientFactory <xref:System.Net.Http.HttpClient> ve [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118))dahil olmak üzere üst düzey ağ API'leri tarafından kullanıldığını da etkiler.

- Varsayılan: <xref:System.Net.Http.SocketsHttpHandler> Kullanım`true`( ).

- Yöntemi çağırarak <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> bu ayarı programlı olarak yapılandırabilirsiniz.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- <xref:System.Net.Http.WinHttpHandler> Linux'ta Windows veya [libcurl](https://curl.haxx.se/libcurl/) kullanımı sağlar |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- kullanımını sağlar<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- <xref:System.Net.Http.WinHttpHandler> Linux'ta Windows veya [libcurl](https://curl.haxx.se/libcurl/) kullanımı sağlar |

> [!NOTE]
> .NET 5'ten `System.Net.Http.UseSocketsHttpHandler` başlayarak, ayar artık kullanılamıyor.
