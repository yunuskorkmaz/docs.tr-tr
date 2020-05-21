---
title: Profil oluşturma yapılandırması ayarları hata ayıklaması
description: .NET Core uygulamaları için hata ayıklamayı ve profil oluşturmayı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761999"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Hata ayıklama ve profil oluşturma için çalışma zamanı yapılandırma seçenekleri

## <a name="enable-diagnostics"></a>Tanılamayı etkinleştirme

- Hata ayıklayıcı, profil oluşturucu ve EventPipe tanılamaları 'nın etkin veya devre dışı olup olmadığını yapılandırır.
- Bu ayarı atlarsanız, Tanılamalar etkinleştirilir. Bu değeri değerine ayarlamaya eşdeğerdir `1` .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_EnableDiagnostics` | `1`-etkin<br/>`0`-devre dışı |

## <a name="enable-profiling"></a>Profil oluşturmayı etkinleştir

- , Çalışmakta olan işlem için profil oluşturmanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.
- Bu ayarı atlarsanız profil oluşturma devre dışı bırakılır. Bu değeri değerine ayarlamaya eşdeğerdir `0` .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | Yok | Yok |
| **Ortam değişkeni** | `CORECLR_ENABLE_PROFILING` | `0`-devre dışı<br/>`1`-etkin |

## <a name="profiler-guid"></a>Profil Oluşturucu GUID 'SI

- O anda çalışan işleme yüklenecek profil oluşturucunun GUID 'sini belirtir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | Yok | Yok |
| **Ortam değişkeni** | `CORECLR_PROFILER` | *dize-GUID* |

## <a name="profiler-location"></a>Profil Oluşturucu konumu

- Şu anda çalışan işleme (veya 32-bit veya 64 bit işlem) yüklenecek profil oluşturucu DLL dosyasının yolunu belirtir.
- Birden fazla değişken ayarlandıysa, bit genişliğine özgü değişkenler öncelik kazanır. Profil oluşturucunun hangi bit hale getirinin yükleneceğini belirler.
- Daha fazla bilgi için bkz. [Profil Oluşturucu kitaplığını bulma](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).

| | Ayar adı | Değerler |
| - | - | - |
| **Ortam değişkeni** | `CORECLR_PROFILER_PATH` | *dize yolu* |
| **Ortam değişkeni** | `CORECLR_PROFILER_PATH_32` | *dize yolu* |
| **Ortam değişkeni** | `CORECLR_PROFILER_PATH_64` | *dize yolu* |

## <a name="write-perf-map"></a>Perf haritasını yaz

- Linux sistemlerinde */t MP/perf-$pid. Map* yazma veya devre dışı bırakır.
- Bu ayarı atlarsanız, perf haritasını yazmak devre dışı bırakılır. Bu değeri değerine ayarlamaya eşdeğerdir `0` .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_PerfMapEnabled` | `0`-devre dışı<br/>`1`-etkin |

## <a name="perf-log-markers"></a>Performans günlüğü işaretçileri

- Belirtilen sinyalin performans günlüklerinde işaret olarak kabul edilip yoksayılmasını sağlar veya devre dışı bırakır.
- Bu ayarı atlarsanız, belirtilen sinyal yok sayılır. Bu değeri değerine ayarlamaya eşdeğerdir `0` .

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_PerfMapIgnoreSignal` | `0`-devre dışı<br/>`1`-etkin |

> [!NOTE]
> [COMPlus_PerfMapEnabled](#write-perf-map) atlanırsa veya `0` (devre dışı) olarak ayarlandıysa bu ayar yoksayılır.
