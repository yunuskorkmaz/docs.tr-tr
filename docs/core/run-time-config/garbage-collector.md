---
title: Çöp toplayıcı config ayarları
description: Çöp toplayıcısının .NET Core uygulamalarının belleği nasıl yönettiğini yapılandırmak için çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607816"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Çöp toplama için çalışma zamanı yapılandırma seçenekleri

Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgiler içerir. Çalışan bir uygulamanın en yüksek performansını elde etmeye çalışıyorsanız, bu ayarları kullanmayı düşünün. Ancak, varsayılanlar, tipik durumlarda çoğu uygulama için en iyi performansı sağlar.

Ayarlar bu sayfada gruplar halinde düzenlenir. Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbiriyle birlikte kullanılır.

> [!NOTE]
>
> - Bu ayarlar çalışırken uygulama tarafından dinamik olarak değiştirilebilir, böylece ayarladığınız çalışma zamanı ayarları geçersiz kılınabilir.
> - [Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar genellikle tasarım zamanında yalnızca API üzerinden ayarlanır. Bu tür ayarlar bu sayfadan atlanır.
> - Sayı değerleri için *runtimeconfig.json* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişken ayarları için hexadecimal gösterimi kullanın. Hexadecimal değerler için, "0x" öneki ile veya olmadan belirtebilirsiniz.

## <a name="flavors-of-garbage-collection"></a>Çöp toplama tatları

Çöp toplamanın iki ana tadı iş istasyonu GC ve sunucu GC vardır. İkisi arasındaki farklar hakkında daha fazla bilgi [için, çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)bölümüne bakın.

Çöp toplama alt tatlar arka plan ve eşzamanlı değildir.

Çöp toplama tatlarını seçmek için aşağıdaki ayarları kullanın:

### <a name="systemgcservercomplus_gcserver"></a>System.GC.Server/COMPlus_gcServer

- Uygulamanın iş istasyonu çöp toplamayı mı yoksa sunucu çöp toplamayı mı kullandığını yapılandırır.
- Varsayılan: İş istasyonu`false`çöp toplama ( ).

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false`- iş istasyonu<br/>`true`- sunucu | .NET Çekirdek 1.0 |
| **MSBuild özelliği** | `ServerGarbageCollection` | `false`- iş istasyonu<br/>`true`- sunucu | .NET Çekirdek 1.0 |
| **Ortam değişkeni** | `COMPlus_gcServer` | `0`- iş istasyonu<br/>`1`- sunucu | .NET Çekirdek 1.0 |
| **.NET Framework için app.config** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`- iş istasyonu<br/>`true`- sunucu |  |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Eşzamanlı/COMPlus_gcConcurrent

- Arka plan (eşzamanlı) çöp toplamanın etkin olup olmadığını yapılandırır.
- Varsayılan: Etkin`true`( ).
- Daha fazla bilgi için Bkz. [Arka Plan çöp toplama](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) ve Arka Plan sunucusu çöp [toplama.](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true`- arka plan GC<br/>`false`- eşzamanlı olmayan GC | .NET Çekirdek 1.0 |
| **MSBuild özelliği** | `ConcurrentGarbageCollection` | `true`- arka plan GC<br/>`false`- eşzamanlı olmayan GC | .NET Çekirdek 1.0 |
| **Ortam değişkeni** | `COMPlus_gcConcurrent` | `true`- arka plan GC<br/>`false`- eşzamanlı olmayan GC | .NET Çekirdek 1.0 |
| **.NET Framework için app.config** | [gcEşzamanlı akım](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`- arka plan GC<br/>`false`- eşzamanlı olmayan GC |  |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>Kaynak kullanımını yönetme

Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.

Bu ayarların bazıları hakkında daha fazla bilgi için [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog girişi arasındaki Orta zemine bakın.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.HeapCount/COMPlus_GCHeapCount

- Çöp toplayıcısı tarafından oluşturulan yığın sayısını sınırlar.
- Yalnızca sunucu çöp toplama için geçerlidir.
- [GC işlemci afinitesi](#systemgcnoaffinitizecomplus_gcnoaffinitize) etkinse, ki bu varsayılan değerdir, `n` yığın sayısı ayarı GC `n` yığınları/iş parçacığı ile ilk işlemcilere affeder. [(Affinitize maskesini](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) veya [affinitize aralıkları](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) ayarlarını kullanarak tam olarak hangi işlemcilerin affinitize olacağını belirtin.)
- [GC işlemci yakınlığı](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışı bırakılırsa, bu ayar GC yığınlarının sayısını sınırlar.
- Daha fazla bilgi için [GCHeapCount açıklamalarına](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)bakın.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapCount` | *hexadecimal değeri* | .NET Core 3.0 |
| **.NET Framework için app.config** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *ondalık değer* | .NET Framework 4.6.2 |

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
> *Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin. Örneğin, yığın sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olacaktır.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMaske/COMPlus_GCHeapAffinitizeMask

- Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.
- [GC işlemci afinitedevre](#systemgcnoaffinitizecomplus_gcnoaffinitize) dışı bırakılırsa, bu ayar yoksayılır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Değer, işlem için kullanılabilir işlemcileri tanımlayan bir bit maskesidir. Örneğin, 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız 0x3FF veya 3FF'nin hexadecimal değeri) ikili gösterimde 0011 1111 1111'dir. Bu, ilk 10 işlemcinin kullanılacağını belirtir. Sonraki 10 işlemciyi belirtmek için, yani 10-19 işlemciler, 1111 1111 1100 0000 0000 ikili değere eşdeğer olan 1047552 (veya 0xFFC00 veya FFC00 hexadecimal değeri) ondalık değerini belirtin.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapAffinitizeMask` | *hexadecimal değeri* | .NET Core 3.0 |
| **.NET Framework için app.config** | [GCHeapAffinitizeMaske](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *ondalık değer* | .NET Framework 4.6.2 |

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

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilistesini belirtir.
- Bu ayar [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)benzer , 64'ten fazla işlemcibelirtmenizi sağlar dışında.
- Windows işletim sistemleri için işlemci numarasını veya aralığını ilgili [CPU grubuyla](/windows/win32/procthread/processor-groups)(örneğin, "0:1-10,0:12,1:50-52,1:70" olarak öneleyin.
- [GC işlemci afinitedevre](#systemgcnoaffinitizecomplus_gcnoaffinitize) dışı bırakılırsa, bu ayar yoksayılır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Daha fazla bilgi için, Maoni Stephens'ın blogunda [64 işlemci> > makinelerde GC için CPU yapılandırması daha iyi hale](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) getirilmesine bakın.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | İşlemci numaralarının veya işlemci numaralarının aralıklarının virgülle ayrılmış listesi.<br/>Unix örnek: "1-10,12,50-52,70"<br/>Windows örneği: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapAffinitizeRanges` | İşlemci numaralarının veya işlemci numaralarının aralıklarının virgülle ayrılmış listesi.<br/>Unix örnek: "1-10,12,50-52,70"<br/>Windows örneği: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |

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

- Çöp toplayıcısının CPU [grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmayacağını yapılandırır.

  64 bit Windows bilgisayarınbirden çok CPU grubu varsa, diğer bir süre 64'ten fazla işlemci vardır ve bu öğenin çöp toplamayı tüm CPU gruplarına yaymasını sağlar. Çöp toplayıcı yığınlar oluşturmak ve dengelemek için tüm çekirdekleri kullanır.

- Yalnızca 64 bit Windows işlem sistemlerinde sunucu çöp toplama için geçerlidir.
- Varsayılan: Devre`0`Dışı ( ).
- Daha fazla bilgi için, Maoni Stephens'ın blogunda [64 işlemci> > makinelerde GC için CPU yapılandırması daha iyi hale](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) getirilmesine bakın.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_GCCpuGroup` | `0`- engelli<br/>`1`- etkin | .NET Çekirdek 1.0 |
| **.NET Framework için app.config** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`- engelli<br/>`true`- etkin |  |

> [!NOTE]
> İş parçacığı havuzundan iş parçacığı tüm CPU gruplarına dağıtmak için ortak dil çalışma süresini (CLR) yapılandırmak için [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin. .NET Core uygulamaları `COMPlus_Thread_UseAllCpuGroups` için, ortam değişkeninin değerini `1`' ye ayarlayarak bu seçeneği etkinleştirebilirsiniz.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- *Çöp* toplama iş parçacığının işlemcilerle uyumlu hale gelip gelmediğini belirtir. Bir GC iş parçacığı affinitize etmek için sadece kendi özel CPU üzerinde çalıştırabilirsiniz anlamına gelir. Her GC iş parçacığı için bir yığın oluşturulur.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Varsayılan: Çöp toplama iş parçacıklarını işlemcilerle`false`affinitize edin ( ).

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false`- affinitize<br/>`true`- affinitize etmeyin | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCNoAffinitize` | `0`- affinitize<br/>`1`- affinitize etmeyin | .NET Core 3.0 |
| **.NET Framework için app.config** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`- affinitize<br/>`true`- affinitize etmeyin | .NET Framework 4.6.2 |

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

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit

- GC yığını ve GC muhasebesi için baytlarda maksimum taahhüt boyutunu belirtir.
- Bu ayar yalnızca 64 bit bilgisayarlar için geçerlidir.
- Yalnızca belirli durumlarda geçerli olan varsayılan değer, 20 MB'dan daha az veya kapsayıcıdaki bellek sınırının %75'i kadardır. Aşağıdaki ler için varsayılan değer uygulanır:

  - İşlem, belirli bir bellek sınırı olan bir kapsayıcı içinde çalışıyor.
  - [System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) ayarlanmaz.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapHardLimit` | *hexadecimal değeri* | .NET Core 3.0 |

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
> *Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin. Örneğin, 200 mebibayt (MiB) bir yığın sabit sınır belirtmek için, değerleri JSON dosyası için 209715200 ve çevre değişkeni için 0xC800000 veya C800000 olacaktır.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- İzin verilebilen GC yığın kullanımını toplam fiziksel belleğin yüzdesi olarak belirtir.
- [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) de ayarlanmışsa, bu ayar yoksayılır.
- Bu ayar yalnızca 64 bit bilgisayarlar için geçerlidir.
- İşlem, belirli bir bellek sınırı olan bir kapsayıcıiçinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.
- Yalnızca belirli durumlarda geçerli olan varsayılan değer, 20 MB'dan daha az veya kapsayıcıdaki bellek sınırının %75'i kadardır. Aşağıdaki ler için varsayılan değer uygulanır:

  - İşlem, belirli bir bellek sınırı olan bir kapsayıcı içinde çalışıyor.
  - [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) ayarlanmaz.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapHardLimitPercent` | *hexadecimal değeri* | .NET Core 3.0 |

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
> *Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin. Örneğin, yığın kullanımını %30 ile sınırlamak için, değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olacaktır.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- Silinmesi gereken segmentlerin ileride kullanılmak üzere bekleme listesine alınıp alınmayacağını veya işletim sistemine (OS) geri salınıp salınmayacağını yapılandırır.
- Varsayılan: Segmentleri işletim sistemine geri`false`bırakın ( ).

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false`- işletim sistemi için sürüm<br/>`true`- beklemeye | .NET Çekirdek 1.0 |
| **MSBuild özelliği** | `RetainVMGarbageCollection` | `false`- işletim sistemi için sürüm<br/>`true`- beklemeye | .NET Çekirdek 1.0 |
| **Ortam değişkeni** | `COMPlus_GCRetainVM` | `0`- işletim sistemi için sürüm<br/>`1`- beklemeye | .NET Çekirdek 1.0 |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>Büyük sayfalar

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Yığın sabit sınır ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.
- Varsayılan: Devre`0`Dışı ( ).
- Bu deneysel bir ayar.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_GCLargePages` | `0`- engelli<br/>`1`- etkin | .NET Core 3.0 |

## <a name="large-objects"></a>Büyük nesneler

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Toplam boyutu 2 gigabayttan (GB) büyük diziler için 64 bit platformlarda çöp toplayıcı desteğini yapılandırır.
- Varsayılan: Etkin`1`( ).
- Bu seçenek ,NET'in gelecekteki sürümünde geçersiz hale gelebilir.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_gcAllowVeryLargeObjects` | `1`- etkin<br/> `0`- engelli | .NET Çekirdek 1.0 |
| **.NET Framework için app.config** | [gcAllowVeryLargeNesneler](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`- etkin<br/> `0`- engelli | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Büyük nesne yığını eşiği

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHThreshold/COMPlus_GCLOHThreshold

- Nesnelerin büyük nesne yığınına (LOH) gitmesine neden olan eşik boyutunu baytlar olarak belirtir.
- Varsayılan eşik 85.000 bayttır.
- Belirttiğiniz değer varsayılan eşiğe göre daha büyük olmalıdır.

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | *ondalık değer* | .NET Çekirdek 1.0 |
| **Ortam değişkeni** | `COMPlus_GCLOHThreshold` | *hexadecimal değeri* | .NET Çekirdek 1.0 |
| **.NET Framework için app.config** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *ondalık değer* |  .NET Framework 4.8 |

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
> *Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin. Örneğin, 120.000 bayt lık bir eşik boyutu ayarlamak için değerler JSON dosyası için 120000 ve ortam değişkeni için 0x1D4C0 veya 1D4C0 olacaktır.

## <a name="standalone-gc"></a>Bağımsız GC

### <a name="complus_gcname"></a>COMPlus_GCName

- Çalışma zamanının yüklemeyi planladığı çöp toplayıcısını içeren kitaplık için bir yol belirtir.
- Daha fazla bilgi için, [Bkz. Bağımsız GC yükleyici tasarımı.](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)

| | Ayar adı | Değerler | Sürüm tanıtıldı |
| - | - | - | - |
| **runtimeconfig.json** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
