---
title: Profil oluşturma config ayarlarını hata ayıklama
description: .NET Core uygulamaları için hata ayıklama ve profil oluşturmayı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802801"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a>Hata ayıklama ve profil oluşturma için çalışma zamanı yapılandırma seçenekleri

## <a name="enable-diagnostics"></a>Tanılamayı etkinleştirme

- Hata ayıklayıcının, profil oluşturucunun ve EventPipe tanılamanın etkin mi yoksa devre dışı mı olduğunu yapılandırır.
- Varsayılan: Etkin`1`( ).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_EnableDiagnostics` | `1`- etkin<br/>`0`- engelli |

## <a name="enable-profiling"></a>Profil oluşturmayı etkinleştirme

- Şu anda çalışan işlem için profil oluşturmanın etkin olup olmadığını yapılandırır.
- Varsayılan: Devre`0`Dışı ( ).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | Yok | Yok |
| **Ortam değişkeni** | `CORECLR_ENABLE_PROFILING` | `0`- engelli<br/>`1`- etkin |

## <a name="profiler-guid"></a>Profiler GUID

- Şu anda çalışan işleme yüklemek için profiloluşturucu GUID belirtir.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | Yok | Yok |
| **Ortam değişkeni** | `CORECLR_PROFILER` | *dize kılavuz* |

## <a name="profiler-location"></a>Profil oluşturucu konumu

- Şu anda çalışan işleme (veya 32-bit veya 64-bit işlem) yüklemek için profil oluşturucu DLL için yol belirtir.
- Birden fazla değişken ayarlanmışsa, bitness'e özgü değişkenler önceliklidir. Profilleyicinin hangi bitliğini yükleyeceklerini belirtirler.
- Daha fazla bilgi için profil [oluşturucu kitaplığını bulma'ya](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)bakın.

| | Ayar adı | Değerler |
| - | - | - |
| **Ortam değişkeni** | `CORECLR_PROFILER_PATH` | *string-yol* |
| **Ortam değişkeni** | `CORECLR_PROFILER_PATH_32` | *string-yol* |
| **Ortam değişkeni** | `CORECLR_PROFILER_PATH_64` | *string-yol* |

## <a name="write-perf-map"></a>Perf haritası yaz

- Linux sistemlerinde */tmp/perf-$pid.map* yazmayı etkinleştirir veya devre dışı kılabilir.
- Varsayılan: Devre`0`Dışı ( ).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_PerfMapEnabled` | `0`- engelli<br/>`1`- etkin |

## <a name="perf-log-markers"></a>Perf günlük işaretleri

- `COMPlus_PerfMapEnabled` Perf `1`günlüklerinde işaretçi olarak kabul edilecek ve yoksayılacak belirtilen sinyali etkinleştirir veya devre dışı eder.
- Varsayılan: Devre`0`Dışı ( ).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_PerfMapIgnoreSignal` | `0`- engelli<br/>`1`- etkin |
