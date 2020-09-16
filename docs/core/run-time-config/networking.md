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
# <a name="run-time-configuration-options-for-networking"></a>Ağ için çalışma zamanı yapılandırma seçenekleri

## <a name="http2-protocol"></a>HTTP/2 Protokolü

- HTTP/2 Protokolü desteğinin etkin olup olmadığını yapılandırır.

- Bu ayarı atlarsanız, HTTP/2 protokolü desteği devre dışı bırakılır. Bu değeri değerine ayarlamaya eşdeğerdir `false` .

- .NET Core 3,0 ' de kullanıma sunulmuştur.

| | Ayar adı | Değerler |
| - | - | - |
| ** Üzerinderuntimeconfig.js** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` -devre dışı<br/>`true` -etkin |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` -devre dışı<br/>`1` -etkin |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>Kullanımlar <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> veya daha eski http protokol yığınları ( <xref:System.Net.Http.WinHttpHandler> Windows 'Da ve `CurlHandler` , Linux üzerinde [libkıvlıya](https://curl.haxx.se/libcurl/)uygulanan bir iç sınıf) olup olmadığını yapılandırır.

  > [!NOTE]
  > Sınıfı doğrudan başlatmak yerine yüksek düzey ağ API 'Leri kullanıyor olabilirsiniz <xref:System.Net.Http.HttpClientHandler> . Bu ayar ayrıca, <xref:System.Net.Http.HttpClient> ve [Httpclientfactory](/previous-versions/aspnet/hh995280(v=vs.118))dahil olmak üzere üst düzey ağ API 'LERI tarafından kullanılan http Protokolü yığınını da etkiler.

- Bu ayarı atlarsanız, <xref:System.Net.Http.HttpClientHandler> kullanır <xref:System.Net.Http.SocketsHttpHandler> . Bu değeri değerine ayarlamaya eşdeğerdir `true` .

- Yöntemini çağırarak bu ayarı programlı bir şekilde yapılandırabilirsiniz <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .

| | Ayar adı | Değerler |
| - | - | - |
| ** Üzerinderuntimeconfig.js** | `System.Net.Http.UseSocketsHttpHandler` | `true` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler><br/>`false` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün |
| **Ortam değişkeni** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` -öğesinin kullanımını etkinleştirilir <xref:System.Net.Http.SocketsHttpHandler><br/>`0` - <xref:System.Net.Http.WinHttpHandler> Linux üzerinde Windows veya [libkıvrımlı](https://curl.haxx.se/libcurl/) kullanımını mümkün |

> [!NOTE]
> .NET 5 ' den başlayarak, `System.Net.Http.UseSocketsHttpHandler` ayar artık kullanılamaz.
