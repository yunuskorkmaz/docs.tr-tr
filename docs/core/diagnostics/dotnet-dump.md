---
title: DotNet-dump-.NET Core
description: DotNet-dump komut satırı aracını yükleme ve kullanma.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 7eba0cba28f0575be4b374b26e9aca26a70df603
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321598"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Döküm toplama ve çözümleme yardımcı programı (`dotnet-dump`)

**Bu makale şu şekilde geçerlidir: ✓** .net Core 3,0 SDK ve sonraki sürümleri

> [!NOTE]
> macOS 'ta `dotnet-dump` desteklenmez.

## <a name="installing-dotnet-dump"></a>@No__t yükleniyor-0

@No__t-0 [NuGet paketinin](https://www.nuget.org/packages/dotnet-dump)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Özeti

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

@No__t-0 genel Aracı, Linux üzerinde `lldb` gibi bir yerel hata ayıklayıcı olmadan Windows ve Linux dökümlerinin toplanması ve çözümlenmesi için bir yoldur. Bu araç, tam olarak çalışan `lldb` olmadığı alp Linux gibi platformlarda önemlidir. @No__t-0 aracı, çökmeleri ve çöp toplayıcıyı (GC) çözümlemek için SOS komutları çalıştırmanızı sağlar, ancak yerel yığın çerçevelerini görüntülemek gibi şeyler desteklenmez.

## <a name="options"></a>Seçenekler

- **`--version`**

  DotNet-Counters yardımcı programının sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                     |
| ------------------------------------------- |
| [DotNet-döküm toplama](#dotnet-dump-collect) |
| [DotNet-döküm Analizi](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>DotNet-döküm toplama

Bir işlemden döküm yakalar.

### <a name="synopsis"></a>Özeti

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut satırı yardımını gösterir.

- **`-p|--process-id <PID>`**

  Kaynağından bir bellek dökümü toplanacak işlem KIMLIĞI sayısını belirtir.

- **`--type <Heap|Mini>`**

  İşlemden toplanan bilgi türlerini belirleyen Dumb türünü belirtir. İki tür vardır:

  - `Heap`-modül listelerini, iş parçacığı listelerini, tüm yığınları, özel durum bilgilerini, tanıtıcı bilgilerini ve eşlenmiş görüntüler hariç tüm belleği içeren büyük ve görece kapsamlı bir döküm.
  - `Mini`-modül listelerini, iş parçacığı listelerini, özel durum bilgilerini ve tüm yığınları içeren küçük bir döküm.

  Belirtilmemişse, varsayılan değer `Heap` ' dır.

- **`-o|--output <output_dump_path>`**

  Toplanan dökümün yazılması gereken tam yol ve dosya adı.

  Belirtilmezse:

  - Windows üzerinde *.\dump_YYYYMMDD_HHMMSS.dmp* varsayılan olarak belirlenmiştir.
  - Linux üzerinde *./core_YYYYMMDD_HHMMSS* varsayılandır.

  YYYYMMDD yıl/ay/gün ve SSMMSS saat/dakika/saniye şeklindedir.

- **`--diag`**

  Döküm toplama tanılama günlüğünü etkinleştir.

## <a name="dotnet-dump-analyze"></a>DotNet-döküm Analizi

Bir dökümü araştırmak için etkileşimli bir kabuk başlatır. Kabuk çeşitli [sos komutlarını](#analyze-sos-commands)kabul eder.

### <a name="synopsis"></a>Özeti

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Arguments

- **`<dump_path>`**

  Analiz edilecek döküm dosyasının yolunu belirtir.

### <a name="options"></a>Seçenekler

- **`-c|--command <debug_command>`**

  Başlatma sırasında kabukta çalıştırılacak [komutu](#analyze-sos-commands) belirtir.

### <a name="analyze-sos-commands"></a>SOS komutlarını çözümle

| Komut                             | İşlev                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Tüm kullanılabilir komutları görüntüler                                                               |
| `soshelp|help <command>`            | Belirtilen komutu görüntüler.                                                               |
| `exit|quit`                         | Etkileşimli moddan çıkar.                                                                       |
| `clrstack <arguments>`              | Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.                                                  |
| `clrthreads <arguments>`            | Çalıştıran yönetilen iş parçacıklarını listeler.                                                            |
| `dumpasync <arguments>`             | Atık toplanan yığında zaman uyumsuz durum makineleri hakkındaki bilgileri görüntüler.                |
| `dumpassembly <arguments>`          | Bir derleme hakkındaki ayrıntıları görüntüler.                                                           |
| `dumpclass <arguments>`             | Belirtilen adresteki bir EE sınıfı yapısı hakkındaki bilgileri görüntüler.                     |
| `dumpdelegate <arguments>`          | Bir temsilciyle ilgili bilgileri görüntüler.                                                        |
| `dumpdomain <arguments>`            | Tüm AppDomain ve etki alanları içindeki tüm derlemelerin bilgilerini görüntüler.                |
| `dumpheap <arguments>`              | Çöp toplanmış yığın ve nesneler hakkında koleksiyon istatistikleri hakkında bilgi görüntüler.       |
| `dumpil <arguments>`                | Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler. |
| `dumplog <arguments>`               | Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar.                         |
| `dumpmd <arguments>`                | Belirtilen adresteki bir MethodDesc yapısıyla ilgili bilgileri görüntüler.                   |
| `dumpmodule <arguments>`            | Belirtilen adresteki bir EE modül yapısıyla ilgili bilgileri görüntüler.                    |
| `dumpmt <arguments>`                | Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler.                           |
| `dumpobj <arguments>`               | Belirtilen adresteki bir nesne hakkındaki bilgileri görüntüler.                                       |
| `dso|dumpstackobjects <arguments>`  | Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.                    |
| `eeheap <arguments>`                | İç çalışma zamanı veri yapıları tarafından tüketilen işlem belleği hakkındaki bilgileri görüntüler.              |
| `finalizequeue <arguments>`         | Sonlandırma için kaydolan tüm nesneleri görüntüler.                                             |
| `gcroot <arguments>`                | Belirtilen adresteki bir nesneye başvurular (veya köklerle) hakkındaki bilgileri görüntüler.              |
| `gcwhere <arguments>`               | Geçirilen bağımsız değişkenin GC yığınındaki konumu görüntüler.                               |
| `ip2md <arguments>`                 | JıT kodundaki belirtilen adreste MethodDesc yapısını görüntüler.                       |
| `histclear <arguments>`             | @No__t-0 komutlarının ailesi tarafından kullanılan tüm kaynakları serbest bırakır.                                |
| `histinit <arguments>`              | Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.                     |
| `histobj <arguments>`               | @No__t-0 ile ilgili çöp toplama stres günlüğü yeniden konumlarını görüntüler.              |
| `histobjfind <arguments>`           | Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.               |
| `histroot <arguments>`              | Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.        |
| `lm|modules`                        | İşlemdeki yerel modülleri görüntüler.                                                   |
| `name2ee <arguments>`               | @No__t-0 için MethodTable yapısını ve EEClass yapısını görüntüler.                |
| `pe|printexception <arguments>`     | @No__t-0 adresindeki özel durum sınıfından türetilmiş tüm nesneleri görüntüler.             |
| `setsymbolserver <arguments>`       | Sembol sunucusu desteğini sunar                                                             |
| `syncblk <arguments>`               | SyncBlock tutucusu bilgilerini görüntüler.                                                           |
| `threads|setthread <threadid>`      | SOS komutlarının geçerli iş parçacığı KIMLIĞINI ayarlar veya görüntüler.                                  |

## <a name="using-dotnet-dump"></a>@No__t kullanma-0

İlk adım bir döküm toplamaktır. Bir temel döküm oluşturulmuşsa bu adım atlanabilir. İşletim sistemi veya .NET Core çalışma zamanının yerleşik [döküm oluşturma özelliği](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) , her biri çekirdek dökümler oluşturabilir.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Şimdi `analyze` komutuyla çekirdek dökümünü çözümleyin:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Bu eylem, şunun gibi komutları kabul eden etkileşimli bir oturum getirir:

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

Uygulamanızı sonlandıran işlenmeyen bir özel durumu görmek için:

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a>Docker için özel yönergeler

Docker altında çalışıyorsanız, döküm toplama `SYS_PTRACE` özellikleri (`--cap-add=SYS_PTRACE` veya `--privileged`) gerektirir.

Microsoft .NET Core SDK Linux Docker görüntülerinde, bazı `dotnet-dump` komutları aşağıdaki özel durumu oluşturabilir:

> İşlenmeyen özel durum: System. DllNotFoundException: paylaşılan ' libdl.so ' kitaplığı veya bağımlılıklarından biri ' özel durumu yüklenemiyor.

Bu sorunu geçici olarak çözmek için "libc6-dev" paketini yüklemelisiniz.
