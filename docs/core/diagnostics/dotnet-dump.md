---
title: dotnet dökümü - .NET Çekirdek
description: Dotnet-dump komut satırı aracını yüklemek ve kullanmak.
ms.date: 10/14/2019
ms.openlocfilehash: 3c0e28d4efc96ae53ec7dfae243725ab400e6b8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737664"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Döküm toplama ve`dotnet-dump`analiz programı ( )

**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler

> [!NOTE]
> `dotnet-dump`macOS'ta desteklenmez.

## <a name="installing-dotnet-dump"></a>Yükleme`dotnet-dump`

`dotnet-dump` [NuGet paketinin](https://www.nuget.org/packages/dotnet-dump)en son sürüm sürümünü yüklemek [için, dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Özet

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

Küresel `dotnet-dump` araç toplamak ve Linux gibi herhangi bir yerli hata ayıklama `lldb` olmadan Windows ve Linux dökümleri analiz etmek için bir yoldur. Bu araç, Alpine Linux gibi tam `lldb` olarak çalışan bir aracın bulunmadığı platformlarda önemlidir. Araç `dotnet-dump` çökmeleri ve çöp toplayıcı (GC) analiz etmek için SOS komutları çalıştırmak için izin verir, ancak yerel yığın çerçeveleri görüntüleme gibi şeyler desteklenmez bu yüzden yerel bir hata ayıklama değildir.

## <a name="options"></a>Seçenekler

- **`--version`**

  Dotnet sayaçları yardımcı programı sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımlarını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                     |
| ------------------------------------------- |
| [dotnet-dökümü toplamak](#dotnet-dump-collect) |
| [dotnet dökümü analiz](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-dökümü toplamak

Bir işlemden bir dökümü yakalar.

### <a name="synopsis"></a>Özet

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut satırı yardımlarını gösterir.

- **`-p|--process-id <PID>`**

  Bellek dökümü toplamak için işlem kimlik numarasını belirtir.

- **`--type <Heap|Mini>`**

  İşlemden toplanan bilgi türlerini belirleyen döküm türünü belirtir. İki türü vardır:

  - `Heap`- Modül listeleri, iş parçacığı listeleri, tüm yığınlar, özel durum bilgileri, işleme bilgileri ve eşlenen görüntüler dışında tüm bellek içeren büyük ve nispeten kapsamlı bir dökümü.
  - `Mini`- Modül listeleri, iş parçacığı listeleri, özel durum bilgileri ve tüm yığınları içeren küçük bir döküm.

  Belirtilmemişse, `Heap` varsayılandır.

- **`-o|--output <output_dump_path>`**

  Toplanan dökümün yazılması gereken tam yol ve dosya adı.

  Belirtilmemişse:

  - *Windows'da .\dump_YYYYMMDD_HHMMSS.dmp* varsayılanları.
  - Linux'ta *./core_YYYYMMDD_HHMMSS* varsayılanları.

  YYYYMMDD Yıl/Ay/Gün ve HHMMSS Saat/Dakika/Saniye'dir.

- **`--diag`**

  Döküm toplama tanılama günlüğe kaydetmeyi sağlar.

## <a name="dotnet-dump-analyze"></a>dotnet dökümü analiz

Bir çöplüğü keşfetmek için etkileşimli bir kabuk başlatır. Kabuk çeşitli [SOS komutları](#analyze-sos-commands)kabul eder.

### <a name="synopsis"></a>Özet

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Bağımsız Değişkenler

- **`<dump_path>`**

  Çözümlemek için döküm dosyasına giden yolu belirtir.

### <a name="options"></a>Seçenekler

- **`-c|--command <debug_command>`**

  Başlangıçta kabukta çalıştırmak için [komutu](#analyze-sos-commands) belirtir.

### <a name="analyze-sos-commands"></a>SOS komutlarını analiz et

| Komut                             | İşlev                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Kullanılabilir tüm komutları görüntüler                                                               |
| `soshelp|help <command>`            | Belirtilen komutu görüntüler.                                                               |
| `exit|quit`                         | İnteraktif moddan çıkar.                                                                       |
| `clrstack <arguments>`              | Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.                                                  |
| `clrthreads <arguments>`            | Çalışan yönetilen iş parçacıklarını listeler.                                                            |
| `dumpasync <arguments>`             | Çöp toplanmış yığında eşit durumu makineleri hakkındaki bilgileri görüntüler.                |
| `dumpassembly <arguments>`          | Derleme yle ilgili ayrıntıları görüntüler.                                                           |
| `dumpclass <arguments>`             | Belirtilen adreste bir EE sınıfı yapısı hakkındaki bilgileri görüntüler.                     |
| `dumpdelegate <arguments>`          | Temsilci hakkındaki bilgileri görüntüler.                                                        |
| `dumpdomain <arguments>`            | Bilgileri tüm AppDomain'leri ve etki alanındaki tüm derlemeleri görüntüler.                |
| `dumpheap <arguments>`              | Çöp toplanmış yığın ve nesnelerle ilgili toplama istatistikleri hakkındaki bilgileri görüntüler.       |
| `dumpil <arguments>`                | Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler. |
| `dumplog <arguments>`               | Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar.                         |
| `dumpmd <arguments>`                | Belirtilen adreste bir MethodDesc yapısı hakkındaki bilgileri görüntüler.                   |
| `dumpmodule <arguments>`            | EE modül yapısı hakkındaki bilgileri belirtilen adreste görüntüler.                    |
| `dumpmt <arguments>`                | Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler.                           |
| `dumpobj <arguments>`               | Belirtilen adreste bir nesne hakkındaki bilgileri görüntüler.                                       |
| `dso|dumpstackobjects <arguments>`  | Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.                    |
| `eeheap <arguments>`                | Dahili çalışma zamanı veri yapıları tarafından tüketilen işlem belleği hakkındaki bilgileri görüntüler.              |
| `finalizequeue <arguments>`         | Sonlandırma için kaydolan tüm nesneleri görüntüler.                                             |
| `gcroot <arguments>`                | Belirtilen adresteki bir nesneye yapılan başvurular (veya kökler) hakkındaki bilgileri görüntüler.              |
| `gcwhere <arguments>`               | Geçirilen bağımsız değişkenin GC yığınındaki konumu görüntüler.                               |
| `ip2md <arguments>`                 | MethodDesc yapısını JIT kodunda belirtilen adreste görüntüler.                       |
| `histclear <arguments>`             | `hist*` Komut ailesi tarafından kullanılan kaynakları serbest bırakır.                                |
| `histinit <arguments>`              | Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.                     |
| `histobj <arguments>`               | 'ye ilişkin çöp toplama stres `<arguments>`günlüğü yer değiştirmelerini görüntüler.              |
| `histobjfind <arguments>`           | Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.               |
| `histroot <arguments>`              | Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.        |
| `lm|modules`                        | İşlemdeki yerel modülleri görüntüler.                                                   |
| `name2ee <arguments>`               | MethodTable yapısını ve EEClass yapısını `<argument>`görüntüler.                |
| `pe|printexception <arguments>`     | Adreste `<argument>`Özel Durum sınıfından türetilen herhangi bir nesneyi görüntüler.             |
| `setsymbolserver <arguments>`       | Sembol sunucu desteğini etkinleştiri                                                             |
| `syncblk <arguments>`               | SyncBlock tutucu bilgilerini görüntüler.                                                           |
| `threads|setthread <threadid>`      | SOS komutları için geçerli iş parçacığı kimliğini ayarlar veya görüntüler.                                  |

## <a name="using-dotnet-dump"></a>`dotnet-dump` kullanma

İlk adım bir çöplük toplamaktır. Çekirdek dökümü zaten oluşturulduysa, bu adım atlanabilir. İşletim sistemi veya .NET Core runtime'ın yerleşik [döküm oluşturma özelliği,](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) her biri çekirdek dökümleri oluşturabilir.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Şimdi `analyze` komutu ile çekirdek dökümü analiz:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Bu eylem gibi komutları kabul eden etkileşimli bir oturum getiriyor:

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

Uygulamanızı öldüren işlenmemiş bir özel durum görmek için:

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

## <a name="special-instructions-for-docker"></a>Docker için özel talimatlar

Docker altında çalışıyorsanız, döküm toplama `SYS_PTRACE` yetenekleri`--cap-add=SYS_PTRACE` (veya) `--privileged`gerektirir.

Microsoft .NET Core SDK Linux `dotnet-dump` Docker görüntülerinde, bazı komutlar aşağıdaki özel durumu atabilir:

> İşlenmemiş özel durum: System.DllNotFoundException: Paylaşılan kitaplığı 'libdl.so' veya bağımlılıklarından biri olan özel durum yükleyemiyor.

Bu sorunu aşmak için "libc6-dev" paketini yükleyin.
