---
title: Aracı kaldır
description: .NET SDK 'larının ve çalışma zamanlarının kontrollü temizlenmesini sağlayan kılavuzlu bir araç olan .NET kaldırma aracına genel bakış.
author: sfoslund
ms.date: 01/28/2021
ms.openlocfilehash: 9afcac150659a8f58a04f4c254b0a0219af42e74
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105440"
---
# <a name="net-uninstall-tool"></a>.NET kaldırma aracı

[.Net kaldırma aracı](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ), bir sistemden .NET SDK 'Ları ve çalışma zamanlarını kaldırmanıza imkan sağlar. Kaldırmak istediğiniz sürümleri belirlemek için bir seçenek koleksiyonu kullanılabilir.

Araç Windows ve macOS 'yi destekler. Linux Şu anda desteklenmiyor.

Bu araç, Windows 'ta yalnızca aşağıdaki yükleyicilerden biri kullanılarak yüklenen SDK 'Ları ve çalışma zamanlarını kaldırabilir:

- .NET SDK ve çalışma zamanı yükleyicisi.
- Visual Studio 2019 sürüm 16,3 ' den önceki sürümlerde Visual Studio yükleyicisi.

MacOS 'ta, araç yalnızca */usr/local/share/DotNet* klasöründe bulunan SDK 'ları ve çalışma zamanlarını kaldırabilir.

Bu sınırlamalar nedeniyle araç, makinenizde tüm .NET SDK 'Ları ve çalışma zamanlarını kaldıramayabilir. `dotnet --info`Bu aracın kaldırakaldıramıyorum SDK 'lar ve çalışma zamanları dahil tüm .NET SDK 'ları ve çalışma zamanlarını bulmak için komutunu kullanabilirsiniz. `dotnet-core-uninstall list`Komut, araçla hangi SDK 'ların kaldırılabileceği görüntülenir. 1,2 ve üzeri sürümleri, SDK ve çalışma zamanlarını sürüm 5,0 veya daha önceki bir sürümü ile kaldırabilir ve aracın önceki sürümleri 3,1 ve önceki sürümlerini kaldırabilir.

## <a name="install-the-tool"></a>Aracı 'nı yükler

.NET kaldırma aracı 'nı [aracın yayınlar sayfasından](https://aka.ms/dotnet-core-uninstall-tool) indirebilir ve [DotNet/CLI-Lab](https://github.com/dotnet/cli-lab) GitHub deposunda kaynak kodu bulabilirsiniz.

> [!NOTE]
> Aracın .NET SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor. Bu nedenle, Windows üzerinde *C:\Program Files* veya MacOS 'ta */usr/local/bin* gibi bir yazma korumalı dizine yüklenmelidir. Ayrıca bkz. [DotNet komutları Için yükseltilmiş erişim](../tools/elevated-access.md). Daha fazla bilgi için bkz. [ayrıntılı yükleme yönergeleri](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Aracı çalıştırma

Aşağıdaki adımlarda, kaldırma aracını çalıştırmak için önerilen yaklaşım gösterilmektedir:

- [1. adım-yüklü .NET SDK 'larını ve çalışma zamanlarını görüntüleme](#step-1---display-installed-net-sdks-and-runtimes)
- [2. adım-bir kuru çalıştırma](#step-2---do-a-dry-run)
- [3. adım-.NET SDK 'larını ve çalışma zamanlarını kaldırma](#step-3---uninstall-net-sdks-and-runtimes)
- [4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-sdks-and-runtimes"></a>1. adım-yüklü .NET SDK 'larını ve çalışma zamanlarını görüntüleme

`dotnet-core-uninstall list`Komutu, bu araçla kaldırılamayan yüklü .NET SDK 'larını ve çalışma zamanlarını listeler. Bazı SDK 'lar ve çalışma zamanları Visual Studio için gerekli olabilir ve bunların kaldırılması önerilmez.

> [!NOTE]
> Komutun çıktısı, `dotnet-core-uninstall list` çoğu durumda çıkış içindeki yüklü sürümlerin listesiyle eşleşmez `dotnet --info` . Özellikle, bu araç ZIP dosyaları tarafından yüklenen veya Visual Studio tarafından yönetilen sürümleri (Visual Studio 2019 16,3 veya üzeri sürümleriyle yüklenmiş herhangi bir sürüm) görüntüleyemez. Bir sürümün Visual Studio tarafından yönetilip yönetilmediğini kontrol etmenin bir yolu `Add or Remove Programs` , Visual Studio tarafından yönetilen sürümlerin görüntüleme adlarında gösterildiği gibi işaretlendiğine göz atın.

**DotNet-çekirdek-kaldırma listesi**

#### <a name="synopsis"></a>Özeti

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Seçenekler

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Bu araçla kaldırılabilecek tüm ASP.NET çalışma zamanlarını listeler.

* **`--hosting-bundle`**

  Bu araçla kaldırılabilecek tüm .NET barındırma paketlerini listeler.

* **`--runtime`**

  Bu araçla kaldırılabilecek tüm .NET çalışma zamanları listeler.

* **`--sdk`**

  Bu araçla kaldırılabilecek tüm .NET SDK 'larını listeler.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `normal` varsayılan değerdir.

* **`--x64`**

  Bu araçla kaldırılabilecek tüm x64 .NET SDK ve çalışma zamanlarını listeler.

* **`--x86`**

  Bu araçla kaldırılabilecek tüm x86 .NET SDK 'larını ve çalışma zamanlarını listeler.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  Bu araçla kaldırılabilecek tüm .NET çalışma zamanları listeler.

* **`--sdk`**

  Bu araçla kaldırılabilecek tüm .NET SDK 'larını listeler.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `normal` varsayılan değerdir.
  
---

#### <a name="examples"></a>Örnekler

* Bu araçla kaldırılabileceği tüm .NET SDK 'Ları ve çalışma zamanlarını listeleyin:

  ```console
  dotnet-core-uninstall list
  ```

* Tüm x64 .NET SDK 'larını ve çalışma zamanlarını listeleyin:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Tüm x86 .NET SDK 'larını listeleyin:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>2. adım-bir kuru çalıştırma

`dotnet-core-uninstall dry-run`Ve `dotnet-core-uninstall whatif` komutları, kaldırma işlemi yapılmadan belirtilen seçeneklere göre kaldırılacak .NET SDK 'larını ve çalışma zamanlarını görüntüler. Bu komutlar eş anlamlılardır.

**DotNet-çekirdek-kaldırma kuru çalıştırma ve DotNet-çekirdek-kaldırma whatIf**

#### <a name="synopsis"></a>Özeti

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Bağımsız değişkenler

* **`VERSION`**

  Kaldırılacak belirtilen sürüm. Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz. Yanıt dosyaları da desteklenir.

  > [!TIP]
  > Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.
  > Bunlar genellikle \* . rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.
  > Bağımsız değişken için bir yanıt dosyası belirtmek için `VERSION` , \@ hemen arkasından yanıt dosyası adı gelen karakteri kullanın.

#### <a name="options"></a>Seçenekler

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-below <VERSION>[ <VERSION>...]`**

  Belirtilen sürümden daha küçük bir sürüme sahip yalnızca .NET SDK 'larını ve çalışma zamanlarını kaldırır. Belirtilen sürüm yüklü durumda kalır.

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  Belirtilen sürümler hariç tüm .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-but-latest`**

  En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-lower-patches`**

  Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır. Bu seçenek global.jskorur.

* **`--all-previews`**

  Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-previews-but-latest`**

  En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--aspnet-runtime`**

  Yalnızca ASP.NET çalışma zamanlarını kaldırır.

* **`--hosting-bundle`**

  Yalnızca .NET çalışma zamanı ve barındırma paketleri kaldırılır.

* **`--major-minor <MAJOR_MINOR>`**

  Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .

* **`--runtime`**

  Yalnızca .NET çalışma zamanlarını kaldırır.

* **`--sdk`**

  Yalnızca .NET SDK 'larını kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `normal` varsayılan değerdir.

* **`--x64`**

  `--sdk` `--runtime` `--aspnet-runtime` X64 SDK 'larını veya çalışma zamanlarını kaldırmak için, ve ile birlikte kullanılmalıdır.

* **`--x86`**

  `--sdk` `--runtime` `--aspnet-runtime` X86 SDK 'larını veya çalışma zamanlarını kaldırmak için ve ile birlikte kullanılmalıdır.

* **`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.

Notlar:

1. ,, Ve yalnızca biri `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` gereklidir.
2. `--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.
3. `--x64`Veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-below <VERSION>[ <VERSION>...]`**

  Belirtilen sürümün altındaki .NET SDK 'larını ve çalışma zamanlarını kaldırır. Belirtilen sürüm kalacak.

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  Bu sürümler dışında .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-but-latest`**

  En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-lower-patches`**

  Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır. Bu seçenek global.jskorur.

* **`--all-previews`**

  Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-previews-but-latest`**

  En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .

* **`--runtime`**

  Yalnızca .NET çalışma zamanlarını kaldırır.

* **`--sdk`**

  Yalnızca .NET SDK 'larını kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `normal` varsayılan değerdir.
  
* **`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.

Notlar:

1. Ve bunlardan yalnızca `--sdk` biri `--runtime` gereklidir.
2. `--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.

---

#### <a name="examples"></a>Örnekler

> [!NOTE]
> Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET SDK 'Ları ve çalışma zamanları çıkışa dahil edilmez `dotnet-core-uninstall dry-run` . Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK ve çalışma zamanlarının bazıları çıkışa dahil edilmeyebilir. Tüm SDK 'Ları ve çalışma zamanlarını dahil etmek için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.

* Daha yüksek düzeltme eklerinin yerini aldığı tüm .NET çalışma zamanlarını kaldırma konusunda Kuru çalıştırın:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Sürümün altındaki tüm .NET SDK 'larını kaldırma konusunda Kuru çalıştırın `2.2.301` :

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-sdks-and-runtimes"></a>3. adım-.NET SDK 'larını ve çalışma zamanlarını kaldırma

`dotnet-core-uninstall remove` bir seçenek koleksiyonuyla belirtilen .NET SDK 'larını ve çalışma zamanlarını kaldırır. 1,2 ve üzeri sürümleri, SDK ve çalışma zamanlarını sürüm 5,0 veya daha önceki bir sürümü ile kaldırabilir ve aracın önceki sürümleri 3,1 ve önceki sürümlerini kaldırabilir.

Bu aracın bozucu bir davranışı olduğundan, Kaldır komutunu çalıştırmadan önce bir kuru çalıştırma yapmanız **önemle** önerilir. Kuru çalıştırma, komutu kullandığınızda hangi .NET SDK 'sının ve çalışma zamanlarının kaldırılacağını gösterir `remove` . Hangi SDK 'ların ve çalışma zamanlarının kaldırılacağını öğrenmek için bkz. [bir sürümü kaldırmalıyım?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) .

> [!CAUTION]
> Aşağıdaki uyarıları aklınızda bulundurun:
>
>- Bu araç, makinenizde bulunan dosyalar için gerekli olan .NET SDK sürümlerini kaldırabilir `global.json` . .NET SDK 'larını [indirme .net](https://dotnet.microsoft.com/download/dotnet) sayfasından yeniden yükleyebilirsiniz.
>- Bu araç, makinenizde bağımlı uygulamalar için gerekli olan .NET çalışma zamanının sürümlerini kaldırabilir. .NET çalışma zamanlarını [.net yükleme](https://dotnet.microsoft.com/download/dotnet) sayfasından yeniden yükleyebilirsiniz.
>- Bu araç, Visual Studio 'nun temel aldığı .NET SDK ve çalışma zamanının sürümlerini kaldırabilir. Visual Studio yüklemenizi ayırırsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisindeki "Onar" ı çalıştırın.

Varsayılan olarak, tüm komutlar, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET SDK 'larını ve çalışma zamanlarını saklar. Bu SDK 'lar ve çalışma zamanları, açıkça bağımsız değişken olarak listelenerek veya seçeneği kullanılarak kaldırılabilir `--force` .

Aracın .NET SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor. Aracı, Windows 'da ve macOS 'ta bulunan bir yönetici komut isteminde çalıştırın `sudo` . `dry-run`Ve `whatif` komutları yükseltme gerektirmez.

**DotNet-çekirdek-kaldırma kaldırma**

#### <a name="synopsis"></a>Özeti

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Bağımsız değişkenler

* **`VERSION`**

  Kaldırılacak belirtilen sürüm. Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz. Yanıt dosyaları da desteklenir.

  > [!TIP]
  > Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.
  > Bunlar genellikle \* . rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.
  > Bağımsız değişken için bir yanıt dosyası belirtmek için `VERSION` , \@ hemen arkasından yanıt dosyası adı gelen karakteri kullanın.

#### <a name="options"></a>Seçenekler

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-below <VERSION>[ <VERSION>...]`**

  Belirtilen sürümden daha küçük bir sürüme sahip yalnızca .NET SDK 'larını ve çalışma zamanlarını kaldırır. Belirtilen sürüm yüklü durumda kalır.

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  Belirtilen sürümler hariç tüm .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-but-latest`**

  En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-lower-patches`**

  Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır. Bu seçenek global.jskorur.

* **`--all-previews`**

  Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-previews-but-latest`**

  En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--aspnet-runtime`**

  Yalnızca ASP.NET çalışma zamanlarını kaldırır.

* **`--hosting-bundle`**

  Yalnızca .NET barındırma paketleri 'ni kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .

* **`--runtime`**

  Yalnızca .NET çalışma zamanlarını kaldırır.

* **`--sdk`**

  Yalnızca .NET SDK 'larını kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `normal` varsayılan değerdir.

* **`--x64`**

  `--sdk` `--runtime` `--aspnet-runtime` X64 SDK 'larını veya çalışma zamanlarını kaldırmak için, ve ile birlikte kullanılmalıdır.

* **`--x86`**

  `--sdk` `--runtime` `--aspnet-runtime` X86 SDK 'larını veya çalışma zamanlarını kaldırmak için ve ile birlikte kullanılmalıdır.

* **`-y, --yes`** Komutu Evet veya onay olmadan yürütür.

* **`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.

Notlar:

1. ,, Ve yalnızca biri `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` gereklidir.
2. `--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.
3. `--x64`Veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-below <VERSION>[ <VERSION>...]`**

  Belirtilen sürümün altındaki .NET SDK 'larını ve çalışma zamanlarını kaldırır. Belirtilen sürüm kalacak.

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  Bu sürümler dışında .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-but-latest`**

  En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--all-lower-patches`**

  Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır. Bu seçenek global.jskorur.

* **`--all-previews`**

  Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.

* **`--all-previews-but-latest`**

  En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.

* **`--major-minor <MAJOR_MINOR>`**

  Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .

* **`--runtime`**

  Yalnızca .NET çalışma zamanlarını kaldırır.

* **`--sdk`**

  Yalnızca .NET SDK 'larını kaldırır.

* **`-v, --verbosity <LEVEL>`**

  Ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `normal` varsayılan değerdir.

* **`-y, --yes`** Komutu Y/N onayına gerek kalmadan yürütür.
  
* **`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.

Notlar:

1. Ve bunlardan yalnızca `--sdk` biri `--runtime` gereklidir.
2. `--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.

---

#### <a name="examples"></a>Örnekler

> [!NOTE]
> Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET SDK 'Ları ve çalışma zamanları tutulur. Aşağıdaki örneklerde, belirtilen SDK ve çalışma zamanlarının bazıları makinenin durumuna bağlı olarak kalabilir. Tüm SDK 'Ları ve çalışma zamanlarını kaldırmak için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.

* `3.0.0-preview6-27804-01`Y/N onayına gerek kalmadan sürüm dışındaki tüm .NET çalışma zamanlarını kaldırın:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Y/n onayı gerekmeden tüm .NET Core 1,1 SDK 'larını kaldırın:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Konsol çıktısı olmadan .NET Core 1.1.11 SDK 'sını kaldırın:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Bu araç tarafından güvenli bir şekilde kaldırılabileceği tüm .NET SDK 'larını kaldırın:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Visual Studio tarafından gerekebilecek SDK 'lar dahil olmak üzere, bu araç tarafından kaldırılabileceği tüm .NET SDK 'larını kaldırın (önerilmez):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Yanıt dosyasında belirtilen tüm .NET SDK 'larını kaldırın `versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  *Versions. rsp* içeriği aşağıdaki gibidir:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)

Bazı durumlarda, artık gerekli değildir `NuGetFallbackFolder` ve silmek isteyebilir. Bu klasörü silme hakkında daha fazla bilgi için bkz. [NuGetFallbackFolder 'ı kaldırma](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Aracı kaldır

## <a name="windows"></a>[Windows](#tab/windows)

1. **Program Ekle veya Kaldır**'ı açın.
2. `Microsoft .NET SDK Uninstall Tool` arayın.
3. **Kaldır**'ı seçin.

## <a name="macos"></a>[macOS](#tab/macos)

İndirilen *DotNet-Core-Uninstall. tar. gz* dosyasını yüklendiği dizinden silin. Bu dosyanın içeriğini başka bir dizine sıkıştırdıysanız, bu içeriği de sildiğinizden emin olun.

---
