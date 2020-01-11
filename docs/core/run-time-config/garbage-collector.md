---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900102"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Çöp toplama için çalışma zamanı yapılandırma seçenekleri

Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir. Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin. Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.

Ayarlar bu sayfadaki gruplar halinde düzenlenir. Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.

> [!NOTE]
>
> - Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.
> - [Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır. Bu tür ayarlar bu sayfadan çıkarılır.
> - Sayı değerleri için, *runtimeconfig. JSON* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişkeni ayarları için onaltılık gösterimi kullanın. Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.

## <a name="flavors-of-garbage-collection"></a>Çöp toplamanın türleri

Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir. İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.

Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.
- Varsayılan: Iş Istasyonu atık toplama (`false`).

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false`-iş istasyonu<br/>`true`-sunucu | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_gcServer` | `0`-iş istasyonu<br/>`1`-sunucu | .NET Core 1,0 |
| **.NET Framework için App. config** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-iş istasyonu<br/>`true`-sunucu |  |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. eşzamanlı/COMPlus_gcConcurrent

- Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.
- Varsayılan: etkin (`true`).
- Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) ve [arka plan sunucusu çöp toplama](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | `true` arka plan GC<br/>`false`-eş zamanlı olmayan GC | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_gcConcurrent` | `true` arka plan GC<br/>`false`-eş zamanlı olmayan GC | .NET Core 1,0 |
| **.NET Framework için App. config** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true` arka plan GC<br/>`false`-eş zamanlı olmayan GC |  |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a>Kaynak kullanımını yönetme

Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.

Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- GC işlemci benzeşimi etkinse, varsayılan olarak, yığın sayısı ayarı GC sayfa@@/iş parçacıklarını ilk `n` işlemcilere `n`. (Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu maskeyi seçin veya aralıklar ayarlarını kesin olarak belirleyin.)
- GC işlemci benzeşimi devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.
- Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapCount` | *onaltılık değer* | .NET Core 3.0 |
| **.NET Framework için App. config** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *ondalık değer* | .NET Framework 4.6.2 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> *Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. ısıpaffinitizemask/COMPlus_GCHeapAffinitizeMask

- Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.
- `System.GC.NoAffinitize` `true`olarak ayarlanarak, işlemci benzeşimi devre dışı bırakıldıysa, bu ayar yoksayılır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir. Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir. Bu, ilk 10 işlemcinin kullanılacağını belirtir. Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapAffinitizeMask` | *onaltılık değer* | .NET Core 3.0 |
| **.NET Framework için App. config** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *ondalık değer* | .NET Framework 4.6.2 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.
- Bu ayar `System.GC.HeapAffinitizeMask`benzerdir, ancak 64 'den fazla işlemciyi belirtmenizi sağlar.
- Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".
- `System.GC.NoAffinitize` `true`olarak ayarlanarak, işlemci benzeşimi devre dışı bırakıldıysa, bu ayar yoksayılır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.<br/>UNIX örneği: "1-10, 12, 50-52, 70"<br/>Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapAffinitizeRanges` | İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.<br/>UNIX örneği: "1-10, 12, 50-52, 70"<br/>Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.

  64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir. Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.

- Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.
- Varsayılan: devre dışı (`0`).
- Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | YOK | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_GCCpuGroup` | `0`-devre dışı<br/>`1` etkin | .NET Core 1,0 |
| **.NET Framework için App. config** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-devre dışı<br/>`true` etkin |  |

> [!NOTE]
> Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin. .NET Core uygulamaları için `COMPlus_Thread_UseAllCpuGroups` ortam değişkeninin değerini `1`olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. Noafınitize/COMPlus_GCNoAffinitize

- *Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir. Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir. Her GC iş parçacığı için bir yığın oluşturulur.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Varsayılan: işlemciler (`false`) ile atık toplama iş parçacıklarını ön olarak başlatma.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false`-afze<br/>`true`-yok etme | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCNoAffinitize` | `0`-afze<br/>`1`-yok etme | .NET Core 3.0 |
| **.NET Framework için App. config** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`-afze<br/>`true`-yok etme | .NET Framework 4.6.2 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapHardLimit` | *onaltılık değer* | .NET Core 3.0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> *Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Toplam belleğin yüzdesi olarak GC yığın kullanımını belirtir.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapHardLimitPercent` | *onaltılık değer* | .NET Core 3.0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> *Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.
- Varsayılan: kesimleri işletim sistemine (`false`) yeniden bırakın.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false`-işletim sistemine yayın<br/>`true`-bekleme üzerine koy| .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_GCRetainVM` | `0`-işletim sistemine yayın<br/>`1`-bekleme üzerine koy | .NET Core 1,0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a>Büyük sayfalar

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.
- Varsayılan: devre dışı (`0`).
- Bu bir deneysel ayardır.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | YOK | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_GCLargePages` | `0`-devre dışı<br/>`1` etkin | .NET Core 3.0 |

## <a name="large-objects"></a>Büyük nesneler

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.
- Varsayılan: etkin (`1`).
- Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | YOK | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_gcAllowVeryLargeObjects` | `1` etkin<br/> `0`-devre dışı | .NET Core 1,0 |
| **.NET Framework için App. config** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1` etkin<br/> `0`-devre dışı | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Büyük nesne yığın eşiği

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System. GC. LOHThreshold/COMPlus_GCLOHThreshold

- Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.
- Varsayılan eşik 85.000 bayttır.
- Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.LOHThreshold` | *ondalık değer* | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_GCLOHThreshold` | *onaltılık değer* | .NET Core 1,0 |
| **.NET Framework için App. config** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *ondalık değer* | .NET Framework 4,8 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> *Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.

## <a name="standalone-gc"></a>Tek başına GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.
- Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **runtimeconfig. JSON** | YOK | YOK | YOK |
| **Ortam değişkeni** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
