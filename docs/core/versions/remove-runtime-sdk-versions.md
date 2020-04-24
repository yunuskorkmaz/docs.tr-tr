---
title: .NET Core çalışma zamanını ve SDK 'sını kaldırma
description: Bu makalede, .NET Core çalışma zamanı ve SDK 'sının hangi sürümlerinin yüklü olduğunu ve sonra Windows, Mac ve Linux 'ta nasıl kaldırılacağını belirleme açıklanmaktadır.
ms.date: 04/22/2020
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 0b3501bf7c730120d3885b8c3f29b901fb131215
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135769"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>.NET Core çalışma zamanı ve SDK 'sını kaldırma

Zaman içinde, .NET Core çalışma zamanının ve SDK 'sının güncelleştirilmiş sürümlerini yüklerken, eski .NET Core sürümlerini makinenizden kaldırmak isteyebilirsiniz. Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürümü seçiminde](selection.md)makalesinde açıklandığı gibi, paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma zamanını değiştirebilir.

## <a name="should-i-remove-a-version"></a>Bir sürümü kaldırmalıyım mıyım?

.NET Core [Sürüm seçimi](selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğu, önceki sürümlerin güvenli şekilde kaldırılmasını mümkün. .NET Core çalışma zamanı güncelleştirmeleri, 1. x ve 2. x gibi ana sürüm ' bantlı ' içinde uyumludur. Ayrıca, .NET Core SDK daha yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturmanıza olanak tanır.

Genel olarak, uygulamanız için gereken çalışma zamanlarının yalnızca en son SDK ve en son düzeltme eki sürümüne ihtiyacınız vardır. Eski SDK veya çalışma zamanı sürümlerinin tutulması, **Project. JSON**tabanlı uygulamaların tutulmasını içerir. Uygulamanızın önceki SDK 'lar veya çalışma zamanları için belirli nedenleri yoksa, eski sürümleri güvenle kaldırabilirsiniz.

## <a name="determine-what-is-installed"></a>Nelerin yüklendiğini belirleme

.NET Core 2,1 ile başlayarak, .NET CLı, makinenizde yüklü olan SDK ve çalışma zamanının sürümlerini listelemek için kullanabileceğiniz seçeneklere sahiptir.  Makinenizde [`dotnet --list-sdks`](../tools/dotnet.md#options) yüklü SDK 'ların listesini görmek için kullanın. Makinenizde [`dotnet --list-runtimes`](../tools/dotnet.md#options) yüklü olan çalışma zamanlarının listesini görmek için kullanın. Aşağıdaki metin Windows, macOS veya Linux için tipik çıktıyı gösterir:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-sdks
```

Aşağıdakine benzer bir çıktı alırsınız:

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

Ve aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakine benzer bir çıktı alırsınız:

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[Linux](#tab/linux)

Aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-sdks
```

Aşağıdakine benzer bir çıktı alırsınız:

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

Ve aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakine benzer bir çıktı alırsınız:

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[Mac OS](#tab/macos)

Aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-sdks
```

Aşağıdakine benzer bir çıktı alırsınız:

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

Ve aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakine benzer bir çıktı alırsınız:

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a>.NET Core kaldır

# <a name="windows"></a>[Windows](#tab/windows)

.NET Core, .NET Core çalışma zamanının ve SDK 'nın sürümlerini kaldırmak için Windows **Program Ekle/Kaldır** iletişim kutusunu kullanır. Aşağıdaki şekilde, .NET çalışma zamanının ve SDK 'nın birkaç sürümü yüklü olan **Program Ekle/Kaldır** iletişim kutusu gösterilmektedir.

![.NET Core kaldırmak için Program Ekle/Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

Makinenizden kaldırmak istediğiniz herhangi bir sürümü seçip **Kaldır**' a tıklayın.

# <a name="linux"></a>[Linux](#tab/linux)

Linux 'ta .NET Core (SDK veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır. .NET Core ' u kaldırmanın en iyi yolu, .NET Core yüklemek için kullandığınız eylemi yansıtmasıdır. Ayrıntılar, seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.

> [!IMPORTANT]
> Red Hat yüklemeleri için, .NET Core 'u yükleme ve kaldırma hakkında bilgi için, [Red Hat kullanmaya başlama kılavuzuna](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) bakın.

.NET Core 2,1 ' den itibaren, bir paket Yöneticisi kullanılarak yükseltilirken .NET Core SDK kaldırmanız gerekmez. Paket Yöneticisi `update` veya `refresh` komutları, daha yeni bir sürümü başarıyla yüklendikten sonra eski sürümü otomatik olarak kaldırır.

.NET Core 'u bir paket Yöneticisi kullanarak yüklediyseniz, .NET SDK veya çalışma zamanı 'nı kaldırmak için aynı paket yöneticisini kullanın. .NET Core yüklemeleri en popüler paket yöneticilerini destekler. Ortamınızdaki kesin bir sözdizimi için dağıtımın Paket Yöneticisi belgelerine başvurun:

- [apt-get (8)](https://linux.die.net/man/8/apt-get) , Ubuntu dahil olmak üzere, dekim tabanlı sistemler tarafından kullanılır.
- Fedora, CentOS ve Oracle Linux için [yılum (8)](https://linux.die.net/man/8/yum) kullanılır.
- [zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) , openSUSE ve SUSE Linux Enterprise System (SLES) ' de kullanılır.
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) , Fedora 'da kullanılır.

Neredeyse tüm durumlarda, bir paketi kaldırma komutu olur `remove`.

Çoğu paket yöneticisi için .NET Core SDK yüklemesinin paket adı ve ardından sürüm numarası `dotnet-sdk`gelir. Çalışma zamanının .NET Core SDK ve sürümünün `2.1` sürümü 2.1.300 başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir: örneğin, .NET Core SDK sürüm 2.1.300, paket `dotnet-sdk-2.1`olarak başvurulabilirler. Önceki sürümler sürüm dizesinin tamamını gerektirir: Örneğin, `dotnet-sdk-2.1.200` .NET Core SDK sürüm 2.1.200 için gerekli olacaktır.

SDK değil yalnızca çalışma zamanını yükleyen makineler için, paket adı `dotnet-runtime-<version>` .NET Core çalışma zamanına ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığınına yöneliktir.

2,0 ' den önceki .NET Core yüklemeleri, SDK Paket Yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı. Kullanarak `apt-get`, komut şu şekilde olur:

```bash
apt-get remove dotnet-host
```

Uygulamasına `dotnet-host`iliştirilmiş bir sürüm olmadığını unutmayın.

Bir tarbol kullanarak yüklediyseniz, el ile yöntemini kullanarak .NET Core 'u kaldırmanız gerekir.

Linux 'ta, sürümlü dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir. Bunun için, bu, SDK ve çalışma zamanının diskten silinmesine neden olur. Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi, `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.

# <a name="macos"></a>[Mac OS](#tab/macos)

Mac üzerinde, sürümlenmiş dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir. Bunun için, bu, SDK ve çalışma zamanının diskten silinmesine neden olur. Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

SDK ve çalışma zamanının üst dizinleri, önceki tabloda gösterildiği gibi, `dotnet --list-sdks` ve `dotnet --list-runtimes` komutunun çıktısında listelenir.

---

## <a name="net-core-uninstall-tool"></a>.NET Core Kaldırma Aracı

[.NET Core kaldırma aracı](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`), bir sistemden .NET Core SDK 'larını ve çalışma zamanlarını kaldırmanıza imkan sağlar. Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>.NET Core SDK sürümlerindeki Visual Studio bağımlılığı

Visual Studio 2019 sürüm 16,3 ' den önce, Visual Studio yükleyicileri tek başına .NET Core SDK yükleyicisini çağırdı. Sonuç olarak, SDK sürümleri Windows **Ekle/Kaldır** iletişim kutusunda görünür. Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK 'larını kaldırmak, Visual Studio 'Yu bozabilir. SDK 'Ları kaldırdıktan sonra Visual Studio sorunları varsa, Visual Studio 'nun söz konusu sürümünde Onar ' ı çalıştırın. Aşağıdaki tabloda .NET Core SDK sürümlerindeki bazı Visual Studio bağımlılıkları gösterilmektedir:

| Visual Studio sürüm | .NET Core SDK sürümü |
| -- | -- |
|  Visual Studio 2019 sürüm 16.2  | .NET Core SDK 2.2.4 xx, 2.1.8 xx |
|  Visual Studio 2019 sürüm 16.1 | .NET Core SDK 2.2.3 xx, 2.1.7 xx |
| Visual Studio 2019 sürüm 16,0 | .NET Core SDK 2.2.2 xx, 2.1.6 xx |
| Visual Studio 2017 sürüm 15,9 | .NET Core SDK 2.2.1 xx, 2.1.5 xx |
| Visual Studio 2017 sürüm 15,8 | .NET Core SDK 2.1.4 xx |

Visual Studio 2019 sürüm 16,3 ' den itibaren, Visual Studio .NET Core SDK kendi kopyasına göre ücretlendirilir. Bu nedenle, bu SDK sürümlerini **Program Ekle/Kaldır** iletişim kutusunda artık göremezsiniz.

## <a name="remove-the-nuget-fallback-folder"></a>NuGet geri dönüş klasörünü kaldır

.NET Core SDK yükleyicileri, .NET Core 3,0 SDK 'dan önce bir NuGet paketleri önbelleğini depolamak için *Nugetfallbackfolder* kullandı. Bu önbellek, `dotnet restore` veya `dotnet build /t:Restore`gibi işlemler sırasında kullanılır. , `NuGetFallbackFolder` Windows üzerinde *C:\Program Files\dotnet\sdk* konumunda ve MacOS 'ta */usr/local/share/DotNet/SDK* konumunda bulunur.

Şu durumlarda bu klasörü kaldırmak isteyebilirsiniz:

* Yalnızca .NET Core 3,0 SDK veya sonraki sürümlerini kullanarak geliştiriyoruz.
* 3,0 'den önceki .NET Core SDK sürümlerini kullanarak geliştiriyoruz, ancak çevrimiçi çalışabilirsiniz ve bir kez daha yavaş çalışabilir.

NuGet geri dönüş klasörünü kaldırmak istiyorsanız, onu silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına sahip olmanız gerekir.

*DotNet* klasörünün silinmesi önerilmez. Bunu yapmak, daha önce yüklediğiniz tüm küresel araçları kaldırır. Ayrıca, Windows üzerinde:

- Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerini bozacaksınız. Kurtarmak için **onarmayı** çalıştırabilirsiniz.
- **Program Ekle/Kaldır** iletişim kutusunda .NET Core SDK girdileri varsa, bunlar yalnız bırakılmış olacaktır.
