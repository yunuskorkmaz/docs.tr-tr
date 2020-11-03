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
# <a name="run-time-configuration-options-for-networking"></a>Ağ için çalışma zamanı yapılandırma seçenekleri

## <a name="http2-protocol"></a>HTTP/2 Protokolü

- HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.

- .NET Core 3,0 ' de kullanıma sunulmuştur.

- Yalnızca .NET Core 3,0: Bu ayarı atlarsanız, HTTP/2 protokolü desteği devre dışı bırakılır. Bu değeri değerine ayarlamaya eşdeğerdir `false` .

- .NET Core 3,1 ve .NET 5 +: Bu ayarı atlarsanız, HTTP/2 Protokolü için destek etkinleştirilir. Bu değeri değerine ayarlamaya eşdeğerdir `true` .

| | Ayar adı | Değerler |
| - | - | - |
| **Üzerinderuntimeconfig.js** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` -devre dışı<br/>`true` -etkin |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` -devre dışı<br/>`1` -etkin |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>Kullanımlar <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya daha eski http protokol yığınları ( <xref:System.Net.Http.WinHttpHandler> Windows 'Da ve `CurlHandler` , Linux üzerinde [libkıvlıya](https://curl.haxx.se/libcurl/)uygulanan bir iç sınıf) olup olmadığını yapılandırır.

  > [!NOTE]
  > Sınıfı doğrudan başlatmak yerine yüksek düzey ağ API 'Leri kullanıyor olabilirsiniz <xref:System.Net.Http.HttpClientHandler> . Bu ayar ayrıca, <xref:System.Net.Http.HttpClient> ve [Httpclientfactory](/previous-versions/aspnet/hh995280(v=vs.118))dahil olmak üzere üst düzey ağ API 'LERI tarafından kullanılan http Protokolü yığınını da etkiler.

- Bu ayarı atlarsanız, <xref:System.Net.Http.HttpClientHandler> kullanır <xref:System.Net.Http.SocketsHttpHandler> . Bu değeri değerine ayarlamaya eşdeğerdir `true` .

- Yöntemini çağırarak bu ayarı programlı bir şekilde yapılandırabilirsiniz <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .

| | Ayar adı | Değerler |
| - | - | - |
| **Üzerinderuntimeconfig.js** | `System.Net.Http.UseSocketsHttpHandler` | `true` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler><br/>`false` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler><br/>`0` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün |

> [!NOTE]
> .NET 5 ' den başlayarak, `System.Net.Http.UseSocketsHttpHandler` ayar artık kullanılamaz.

## <a name="latin1-headers-net-core-31-only"></a>Latin1 üstbilgileri (yalnızca .NET Core 3,1)

- Bu anahtar, <xref:System.Net.Http.SocketsHttpHandler> üst BILGIDE ISO-8859-1 (Latin-1) kodlu karakter gönderilmesini sağlayan http üst bilgi doğrulamasını yeniden sağlamayı sağlar.

- Bu ayarı atlarsanız, ASCII olmayan bir karakter gönderme girişimi buna neden olur <xref:System.Net.Http.HttpRequestException> . Bu değeri değerine ayarlamaya eşdeğerdir `false` .

| | Ayar adı | Değerler |
| - | - | - |
| **Üzerinderuntimeconfig.js** | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | `false` -devre dışı<br/>`true` -etkin |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | `0` -devre dışı<br/>`1` -etkin |

> [!NOTE]
> Bu seçenek, önceki veya sonraki sürümlerde değil, .NET Core 3,1 sürümünde 3.1.9 sürümünden itibaren kullanılabilir. .NET 5 ' te kullanmanızı öneririz <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> .
