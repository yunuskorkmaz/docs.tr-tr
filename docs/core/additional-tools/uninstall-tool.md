---
title: Aracı Kaldır
description: .NET Core SDK'ların ve çalışma saatlerinin kontrollü olarak temizlenmesini sağlayan kılavuzlu bir araç olan .NET Çekirdek Kaldırma Aracı'na genel bir bakış.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847096"
---
# <a name="net-core-uninstall-tool"></a>.NET Core Kaldırma Aracı

[.NET Çekirdek Kaldırma](https://aka.ms/dotnet-core-uninstall-tool) Aracı`dotnet-core-uninstall`( ) bir sistemden .NET Core SDK'ları ve Runtimes'ı kaldırmanızı sağlar. Hangi sürümleri kaldırmak istediğinizi belirtmek için seçenekler topluluğu kullanılabilir.

Araç Windows ve macOS'u destekler. Linux şu anda desteklenmez.

Windows'da araç yalnızca aşağıdaki yükleyicilerden birini kullanarak yüklenen SDK'ları ve Çalışma Sürelerini kaldırabilir:

- .NET Core SDK ve çalışma zamanı yükleyici.
- Visual Studio 2019 sürüm 16.3 daha önceki sürümlerinde Visual Studio yükleyici.

macOS'ta araç yalnızca */usr/local/share/dotnet* klasöründe bulunan SDK'ları ve çalışma sürelerini kaldırabilir.

Bu sınırlamalar nedeniyle, araç makinenizdeki .NET Core SDK'ların ve çalışma sürelerinin tümünün yüklenmesini kaldıramayabilir. Bu sdk'lar ve bu aracın kaldıramayacağı çalışma saatleri de dahil olmak üzere, yüklü tüm .NET Core SDK'ları ve çalışma sürelerini bulmak için `dotnet --info` komutu kullanabilirsiniz. Komut, `dotnet-core-uninstall list` araçla birlikte SDK'ların kaldırAbileceği komutu görüntüler.

## <a name="install-the-tool"></a>Aracı yükleme

.NET Çekirdek Kaldırma Aracı'nı [buradan](https://aka.ms/dotnet-core-uninstall-tool) indirebilir ve kaynak kodunu [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub deposunda bulabilirsiniz.

> [!NOTE]
> Araç .NET Core SDK'ları ve çalışma sürelerini kaldırmak için yükseklik gerektirir. Bu nedenle, Windows'daki *C:\Program Files* veya macOS'taki */usr/local/bin* gibi yazma korumalı bir dizine yüklenmelidir. Ayrıca [bakınız Dotnet komutları için yükseltilmiş erişim.](../tools/elevated-access.md) Daha fazla bilgi için [ayrıntılı yükleme yönergelerine](https://aka.ms/dotnet-core-uninstall-tool)bakın.

## <a name="run-the-tool"></a>Aracı çalıştırma

Aşağıdaki adımlar, kaldırma aracını çalıştırmak için önerilen yaklaşımı gösterir:

- [Adım 1 - Ekran yüklü .NET Core SDK'lar ve çalışma süreleri](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Adım 2 - Kuru bir çalışma yapın](#step-2---do-a-dry-run)
- [Adım 3 - .NET Çekirdek SDK'ları ve Çalışma Sürelerini Kaldır](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Adım 4 - NuGet geri dönüş klasörünü silin (isteğe bağlı)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Adım 1 - Ekran yüklü .NET Core SDK'lar ve çalışma süreleri

Komut, `dotnet-core-uninstall list` yüklenen .NET Core SDK'ları ve bu araçla kaldırılabilen çalışma sürelerini listeler. Bazı SDK'lar ve çalışma süreleri Visual Studio tarafından gerekli olabilir ve bunları kaldırmak için tavsiye edilmez neden bir not ile görüntülenir.

**dotnet-core-uninstall listesi**

#### <a name="synopsis"></a>Özet

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Seçenekler

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Bu araçla kaldırılabilen tüm ASP.NET Core çalışma sürelerini listeler.

* **`--hosting-bundle`**

  Bu araçla kaldırılabilen tüm .NET Core çalışma süresini ve barındırma paketlerini listeler.

* **`--runtime`**

  Bu araçla kaldırılabilen tüm .NET Core çalışma saatlerini listeler.

* **`--sdk`**

  Bu araçla kaldırılabilen tüm .NET Core SDK'ları listeler.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntılı lık düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.

* **`--x64`**

  Bu araçla kaldırılabilen tüm x64 .NET Core SDK'ları ve çalışma sürelerini listeler.

* **`--x86`**

  Bu araçla kaldırılabilen tüm x86 .NET Core SDK'ları ve çalışma sürelerini listeler.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--runtime`**

  Bu araçla kaldırılabilen tüm .NET Core çalışma saatlerini listeler.

* **`--sdk`**

  Bu araçla kaldırılabilen tüm .NET Core SDK'ları listeler.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntılı lık düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.
  
---

#### <a name="examples"></a>Örnekler

* Bu araçla kaldırılabilen tüm .NET Core SDK'ları ve çalışma sürelerini listele:

  ```console
  dotnet-core-uninstall list
  ```

* Tüm x64 .NET Core SDK'ları ve çalışma sürelerini listele:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Tüm x86 .NET Çekirdek SDK'larını listele:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Adım 2 - Kuru bir çalışma yapın

Ve `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` komutları,.NET Core SDK'ları ve kaldırma gerçekleştirmeden sağlanan seçeneklere göre kaldırılacak çalışma sürelerini görüntüler. Bu komutlar eş anlamlıdır.

**dotnet-core-install kuru çalıştır ve dotnet-core-uninstall whatif**

#### <a name="synopsis"></a>Özet

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

* **`VERSION`**

  Kaldırmak için belirtilen sürüm. Boşluklara göre ayrılmış birkaç sürümü birbiri ardına listeleyebilirsiniz. Yanıt dosyaları da desteklenir.

  > [!TIP]
  > Yanıt dosyaları, tüm sürümleri komut satırına yerleştirmek için bir alternatiftir.
  > Bunlar genellikle \*.rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.
  > `VERSION` Bağımsız değişken için yanıt dosyası belirtmek \@ için, yanıt dosyası adını hemen izleyen karakteri kullanın.

#### <a name="options"></a>Seçenekler

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-below <VERSION>`**

  Yalnızca .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümden daha küçük bir sürümle kaldırır. Belirtilen sürüm yüklü kalır.

* **`--all-but <VERSIONS>`**

  Belirtilen sürümler dışında tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-but-latest`**

  .NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.

* **`--all-lower-patches`**

  .NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır. Bu seçenek global.json'ı korur.

* **`--all-previews`**

  .NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--all-previews-but-latest`**

  .NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--aspnet-runtime`**

  Yalnızca Core çalışma sürelerini ASP.NET kaldırır.

* **`--hosting-bundle`**

  .NET Core çalışma süresini ve yalnızca barındırma paketlerini kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  .NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.

* **`--runtime`**

  Yalnızca .NET Core çalışma sürelerini kaldırır.

* **`--sdk`**

  Yalnızca .NET Core SDK'ları kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntılı lık düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.

* **`--x64`**

  `--sdk`X64 `--runtime` `--aspnet-runtime` SDK'lar veya çalışma süreleri ile kullanılmalıdır.

* **`--x86`**

  `--sdk`X86 SDK'ları veya çalışma sürelerini kaldırmak `--aspnet-runtime` için , ve `--runtime`kullanılmalıdır.

* **`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.

Notlar:

1. Tam olarak `--sdk` `--runtime`biri `--aspnet-runtime`, `--hosting-bundle` , , ve gereklidir.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.
3. Belirtilmemişse `--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-below <VERSION>`**

  .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümün altında kaldırır. Belirtilen sürüm kalır.

* **`--all-but <VERSIONS>`**

  Belirtilen sürümler dışında .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-but-latest`**

  .NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.

* **`--all-lower-patches`**

  .NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır. Bu seçenek global.json'ı korur.

* **`--all-previews`**

  .NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--all-previews-but-latest`**

  .NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  .NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.

* **`--runtime`**

  Yalnızca .NET Core çalışma sürelerini kaldırır.

* **`--sdk`**

  Yalnızca .NET Core SDK'ları kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntılı lık düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.
  
* **`--force`** Visual Studio veya SDK'lar tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.

Notlar:

1. Tam olarak `--sdk` `--runtime` biri ve gereklidir.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.

---

#### <a name="examples"></a>Örnekler

> [!NOTE]
> Varsayılan olarak, .NET Core SDK'lar ve Visual Studio veya diğer SDK'lar tarafından `dotnet-core-uninstall dry-run` gerekli olabilecek çalışma süreleri çıktıya dahil edilmez. Aşağıdaki örneklerde, makinenin durumuna bağlı olarak, belirtilen SDK'lardan ve çalışma sürelerinden bazıları çıktıya dahil edilemez. Tüm SDK'ları ve çalışma sürelerini eklemek için bunları `--force` açıkça bağımsız değişken olarak listeleyin veya seçeneği kullanın.

* Daha yüksek yamalar tarafından yerini almış tüm .NET Core runtimes kaldırma kuru çalışma:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Sürüm `2.2.301`altındaki tüm .NET Core SDK'ları kaldırmanın kuru çalıştırılması:

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Adım 3 - .NET Çekirdek SDK'ları ve Çalışma Sürelerini Kaldır

`dotnet-core-uninstall remove`bir seçenek koleksiyonu tarafından belirtilen .NET Core SDK'ları ve Runtimes'ı yükler. Araç, Sürüm 5.0 veya üzeri sürümile SDK'ları ve Runtimes'ı kaldırmak için kullanılamaz.

Bu araç yıkıcı bir davranışa sahip olduğundan, kaldırma komutunu çalıştırmadan önce kuru bir çalışma yapmanız **önerilir.** Kuru çalıştırma, `remove` komutu kullandığınızda .NET Core SDK'ların ve çalışma sürelerinin ne kadar kaldırılacağını gösterir. Hangi SDK'ların ve çalışma sürelerinin kaldırılmasının güvenli olduğunu öğrenmek için [bir sürümü kaldırmam gerekir mi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)

> [!CAUTION]
> Aşağıdaki uyarılara dikkat edin:
>
>- Bu araç, makinenizdeki dosyalar tarafından `global.json` gerekli olan .NET Core SDK sürümlerini kaldırabilir. .NET Core SDK'larını [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.
>- Bu araç, .NET Core çalışma zamanının, makinenizdeki çerçeveye bağımlı uygulamalar tarafından gerekli olan sürümlerini kaldırabilir. .NET Core çalışma saatlerini [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.
>- Bu araç, .NET Core SDK sürümlerini ve Visual Studio'nun güvendiği çalışma süresini kaldırabilir. Visual Studio yüklemenizi bozarsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisinde "Onarım"ı çalıştırın.

Varsayılan olarak, tüm komutlar .NET Core SDK'larını ve Visual Studio veya diğer SDK'lar tarafından gerekli olabilecek çalışma sürelerini tutar. Bu SDK'lar ve çalışma süreleri, bunları açıkça bağımsız değişken olarak `--force` listeleyerek veya seçeneği kullanarak kaldırılabilir.

Araç .NET Core SDK'ları ve çalışma sürelerini kaldırmak için yükseklik gerektirir. Aracı Windows'da ve `sudo` macOS'ta bir Yönetici komut isteminde çalıştırın. Ve `dry-run` `whatif` komutları yükseklik gerektirmez.

**dotnet-core-uninstall kaldırma**

#### <a name="synopsis"></a>Özet

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

* **`VERSION`**

  Kaldırmak için belirtilen sürüm. Boşluklara göre ayrılmış birkaç sürümü birbiri ardına listeleyebilirsiniz. Yanıt dosyaları da desteklenir.

  > [!TIP]
  > Yanıt dosyaları, tüm sürümleri komut satırına yerleştirmek için bir alternatiftir.
  > Bunlar genellikle \*.rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.
  > `VERSION` Bağımsız değişken için yanıt dosyası belirtmek \@ için, yanıt dosyası adını hemen izleyen karakteri kullanın.

#### <a name="options"></a>Seçenekler

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-below <VERSION>`**

  Yalnızca .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümden daha küçük bir sürümle kaldırır. Belirtilen sürüm yüklü kalır.

* **`--all-but <VERSIONS>`**

  Belirtilen sürümler dışında tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-but-latest`**

  .NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.

* **`--all-lower-patches`**

  .NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır. Bu seçenek global.json'ı korur.

* **`--all-previews`**

  .NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--all-previews-but-latest`**

  .NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--aspnet-runtime`**

  Yalnızca Core çalışma sürelerini ASP.NET kaldırır.

* **`--hosting-bundle`**

  .NET Core çalışma süresini ve yalnızca barındırma paketlerini kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  .NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.

* **`--runtime`**

  Yalnızca .NET Core çalışma sürelerini kaldırır.

* **`--sdk`**

  Yalnızca .NET Core SDK'ları kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntılı lık düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.

* **`--x64`**

  `--sdk`X64 `--runtime` `--aspnet-runtime` SDK'lar veya çalışma süreleri ile kullanılmalıdır.

* **`--x86`**

  `--sdk`X86 SDK'ları veya çalışma sürelerini kaldırmak `--aspnet-runtime` için , ve `--runtime`kullanılmalıdır.

* **`-y, --yes`** Evet veya hayır onayı gerektirmeden komutu yürütür.

* **`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.

Notlar:

1. Tam olarak `--sdk` `--runtime`biri `--aspnet-runtime`, `--hosting-bundle` , , ve gereklidir.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.
3. Belirtilmemişse `--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-below <VERSION>`**

  .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümün altında kaldırır. Belirtilen sürüm kalır.

* **`--all-but <VERSIONS>`**

  Belirtilen sürümler dışında .NET Core SDK'ları ve çalışma sürelerini kaldırır.

* **`--all-but-latest`**

  .NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.

* **`--all-lower-patches`**

  .NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır. Bu seçenek global.json'ı korur.

* **`--all-previews`**

  .NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--all-previews-but-latest`**

  .NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  .NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.

* **`--runtime`**

  Yalnızca .NET Core çalışma sürelerini kaldırır.

* **`--sdk`**

  Yalnızca .NET Core SDK'ları kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntılı lık düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `normal`.

* **`-y, --yes`** Y/N onayı gerektirmeden komutu yürütür.
  
* **`--force`** Visual Studio veya SDK'lar tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.

Notlar:

1. Tam olarak `--sdk` `--runtime` biri ve gereklidir.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.

---

#### <a name="examples"></a>Örnekler

> [!NOTE]
> Varsayılan olarak, .NET Core SDK'lar ve Visual Studio veya diğer SDK'lar tarafından gerekli olabilecek çalışma süreleri tutulur. Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK'lardan ve çalışma sürelerinden bazıları kalabilir. Tüm SDK'ları ve çalışma sürelerini kaldırmak için bunları `--force` açıkça bağımsız değişken olarak listeleyin veya seçeneği kullanın.

* Y/N onayı gerektirmeden sürüm `3.0.0-preview6-27804-01` dışındaki tüm .NET Core çalışma sürelerini kaldırın:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Y/n onayı gerektirmeden tüm .NET Core 1.1 SDK'larını kaldırın:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* .NET Core 1.1.11 SDK konsol çıkışı olmadan kaldırın:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Bu araç tarafından güvenli bir şekilde çıkarılabilen tüm .NET Core SDK'larını kaldırın:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Visual Studio tarafından gerekli olabilecek SDK'lar da dahil olmak üzere bu araç tarafından kaldırılabilecek tüm .NET Core SDK'larını kaldırın (önerilmez):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Yanıt dosyasında belirtilen tüm .NET Core SDK'ları kaldırma`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  *versions.rsp* içeriği aşağıdaki gibidir:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Adım 4 - NuGet geri dönüş klasörünü silin (isteğe bağlı)

Bazı durumlarda, artık ihtiyacınız `NuGetFallbackFolder` yok ve silmek isteyebilirsiniz. Bu klasörü silme hakkında daha fazla bilgi için [NuGetFallbackFolder'ı Kaldır'a](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)bakın.

## <a name="uninstall-the-tool"></a>Aracı kaldırma

## <a name="windows"></a>[Windows](#tab/windows)

1. **Program Ekle veya Kaldır'ı**aç.
2. `Microsoft .NET Core SDK Uninstall Tool` arayın.
3. **Kaldır**'ı seçin.

## <a name="macos"></a>[Macos](#tab/macos)

İndirilen *dotnet-core-uninstall.tar.gz* dosyasını yüklendiği dizinden silin. Bu dosyanın içeriğini başka bir dizine açtıysanız, bu içeriği de sildiğimden emin olun.

---
