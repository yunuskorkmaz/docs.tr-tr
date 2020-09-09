---
title: Linux dökümlerinde hata ayıkla
description: Bu makalede, Linux ortamlarından dökümleri nasıl toplayacağınızı ve analiz edeceğinizi öğreneceksiniz.
ms.date: 08/27/2020
ms.openlocfilehash: d62295e165f56e32ef73ab628ca9ebd77a4435d1
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598357"
---
# <a name="debug-linux-dumps"></a>Linux dökümlerinde hata ayıkla

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,0 SDK ve sonraki sürümleri

## <a name="collect-dumps-on-linux"></a>Linux üzerinde dökümleri topla

Linux üzerinde dökümler toplamanın iki önerilen yolu [`dotnet-dump`](dotnet-dump.md) veya [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) araçlardır.

### <a name="managed-dumps-with-dotnet-dump"></a>İle yönetilen dökümler `dotnet-dump`

[`dotnet-dump`](dotnet-dump.md)Aracın kullanımı basittir ve herhangi bir yerel hata ayıklayıcıya bağımlılığı yoktur. `dotnet-dump` geleneksel hata ayıklama araçlarının kullanılamadığı çok sayıda Linux platformunda (alp veya ARM32/ARM64 gibi) çalışmaktadır. Ancak, `dotnet-dump` yalnızca yönetilen durumu yakalar, bu nedenle yerel koddaki hata ayıklama sorunları için kullanılamaz. Tarafından toplanan dökümler, `dotnet-dump` dökümün oluşturulduğu işletim sistemi ve mimariye sahip bir ortamda çözümlenir. [`dotnet-gcdump`](dotnet-gcdump.md)Araç yalnızca GC yığın bilgilerini yakalayan, ancak Windows üzerinde çözümlenebilecek dökümler üreten bir alternatif olarak kullanılabilir.

### <a name="core-dumps-with-createdump"></a>İle temel dökümler `createdump`

`dotnet-dump`Yalnızca yönetilen dökümler oluşturan diğer seçenek, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) Linux üzerinde hem yerel hem de yönetilen bilgiler içeren çekirdek dökümler oluşturmak için önerilen araçtır. GDB veya gcore gibi diğer araçlar da temel dökümler oluşturmak için kullanılabilir ancak yönetilen hata ayıklama için gereken durumu kaçırabilir ve analiz sırasında "BILINMEYEN" tür veya işlev adlarına neden olabilir.

`createdump`Araçlar .NET Core çalışma zamanı ile yüklenir ve libcoreclr.so ' nin yanında (genellikle "/usr/share/DotNet/Shared/Microsoft.NETCore.app/[Version]" içinde) bulunabilir. Araç, birincil bağımsız değişkeni olarak döküm toplamak için bir işlem KIMLIĞI alır ve toplanacak döküm türünü belirten isteğe bağlı parametreleri de alabilir (yığın içeren bir mini döküm varsayılandır). Seçeneklere şunlar dahildir:

- **`<input-filename>`**

  Dönüştürülecek giriş izleme dosyası. *Trace. NetTrace*için varsayılanlar.

### <a name="options"></a>Seçenekler

- **`-f|--name <output-filename>`**

  Döküm yazılacak dosya. Varsayılan değer, hedef işlemin işlem KIMLIĞI olan% p olan '/tmp/coredump.%p '.

- **`-n|--normal`**

  Mini döküm oluştur.

- **`-h|--withheap`**

  Yığın ile bir mini döküm oluştur (varsayılan).

- **`-t|--triage`**

  Önceliklendirme mini döküm dosyası oluşturma.

- **`-u|--full`**

  Tam çekirdek dökümü oluşturun.

- **`-d|--diag`**

  Tanılama iletilerini etkinleştirin.

Çekirdek dökümlerinin toplanması, `SYS_PTRACE` özelliği ya da `createdump` sudo veya su ile çalıştırılmasını gerektirir.

## <a name="analyze-dumps-on-linux"></a>Linux 'ta dökümleri çözümleme

İle toplanan yönetilen dökümler `dotnet-dump` ve ile toplanan temel dökümler, `createdump` `dotnet-dump` komutu kullanılarak araçla analiz edilebilir `dotnet-dump analyze` . , `dotnet dump` Dökümünü çözümleyen ortamın, dökümün yakalandığı ortamla aynı işletim sistemine ve mimariye sahip olmasını gerektirir.

Alternatif olarak, hem yönetilen hem de yerel çerçevelerin analizine olanak tanıyan Linux üzerinde çekirdek dökümlerini çözümlemek için [Lldb](https://lldb.llvm.org/) kullanılabilir. LLDB, yönetilen kodun hatalarını ayıklamak için SOS uzantısını kullanır. [`dotnet-sos`](dotnet-sos.md)CLI Aracı, yönetilen kodda hata ayıklama için [birçok yararlı komuta](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) sahip sos 'yi yüklemek için kullanılabilir. .NET Core dökümlerini çözümlemek için, LLDB ve SOS, döküm oluşturulan ortamdan aşağıdaki .NET Core ikililerini gerektirir:

1. libmscordaccore.so
2. libcoreclr.so
3. DotNet (uygulamayı başlatmak için kullanılan ana bilgisayar)

Çoğu durumda, bu ikili dosyalar araç kullanılarak indirilebilir [`dotnet-symbol`](dotnet-symbol.md) . Gerekli ikililer ile indirilemez `dotnet-symbol` (örneğin, kaynaktan oluşturulan özel bir .NET Core sürümü kullanılıyorsa), yukarıda listelenen dosyaları dökümün oluşturulduğu ortamdan kopyalamak gerekebilir. Dosyalar döküm dosyasının yanında bulunmuyorsa, ' `setclrpath <path>` den yüklenmesi gereken yolu ayarlamak ve `setsymbolserver -directory <path>` sembol dosyaları için aranacak yolu ayarlamak için lldb/sos komutunu kullanabilirsiniz.

Gerekli dosyalar kullanılabilir olduğunda, hata ayıklaması yapılacak yürütülebilir dosya olarak DotNet ana bilgisayarı belirtilerek, döküm LLDB 'ye yüklenebilir:

```console
lldb --core <dump-file> <host-program>
```

Yukarıdaki komut satırında, `<dump-file>` analiz edilecek döküm yoludur ve `<host-program>` .NET Core uygulamasını Başlatan yerel programdır. `dotnet`Uygulama kendi kendine dahil olmadığı müddetçe genellikle ikili bir durumdur, bu durumda dll uzantısı olmayan uygulamanın adıdır.

LLDB başladıktan sonra, `setsymbolserver` komutun doğru sembol konumunu işaret etmek için ( `setsymbolserver -ms` Microsoft 'un sembol sunucusunu kullanmak veya `setsymbolserver -directory <path>` yerel bir yol belirtmek için) kullanılması gerekebilir. Yerel semboller çalıştırılarak çalıştırılabilir `loadsymbols` . Bu noktada, dökümünü çözümlemek için [sos komutları](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- , SOS uzantısını yükleme hakkında daha fazla bilgi için [DotNet-sos](dotnet-sos.md) .
- [DotNet-](dotnet-symbol.md) sembol indirme aracını yükleme ve kullanma hakkında daha fazla ayrıntı için.
- Yararlı bir SSS dahil olmak üzere hata ayıklama hakkında daha fazla ayrıntı için [.NET Core tanılama deposu](https://github.com/dotnet/diagnostics/blob/master/documentation/) .
- Lldb 'yi Linux veya Mac 'e yükleme yönergeleri için [yükleme](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) .
