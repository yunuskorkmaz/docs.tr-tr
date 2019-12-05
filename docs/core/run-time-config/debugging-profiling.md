---
title: Profil oluşturma yapılandırması ayarları hata ayıklaması
description: .NET Core uygulamaları için hata ayıklamayı ve profil oluşturmayı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802801"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Hata ayıklama ve profil oluşturma için çalışma zamanı yapılandırma seçenekleri

## <a name="enable-diagnostics"></a>Tanılamayı etkinleştirme

- Hata ayıklayıcı, profil oluşturucu ve EventPipe tanılamaları 'nın etkin veya devre dışı olup olmadığını yapılandırır.
- Varsayılan: etkin (`1`).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_EnableDiagnostics` | `1` etkin<br/>`0`-devre dışı |

## <a name="enable-profiling"></a>Profil oluşturmayı etkinleştir

- , Çalışmakta olan işlem için profil oluşturmanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.
- Varsayılan: devre dışı (`0`).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | YOK | YOK |
| **Ortam değişkeni** | `CORECLR_ENABLE_PROFILING` | `0`-devre dışı<br/>`1` etkin |

## <a name="profiler-guid"></a>Profil Oluşturucu GUID 'SI

- O anda çalışan işleme yüklenecek profil oluşturucunun GUID 'sini belirtir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | YOK | YOK |
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
- Varsayılan: devre dışı (`0`).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_PerfMapEnabled` | `0`-devre dışı<br/>`1` etkin |

## <a name="perf-log-markers"></a>Performans günlüğü işaretçileri

- `COMPlus_PerfMapEnabled` `1`olarak ayarlandığında, belirtilen sinyalin performans günlüklerinde işaret olarak kabul edilip yoksayılmasını sağlar veya devre dışı bırakır.
- Varsayılan: devre dışı (`0`).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_PerfMapIgnoreSignal` | `0`-devre dışı<br/>`1` etkin |
