---
title: .NET Core çalışma zamanını ve SDK 'sını kaldırma
description: Bu makalede, .NET Core çalışma zamanı ve SDK 'sının hangi sürümlerinin yüklü olduğunu ve sonra Windows, Mac ve Linux 'ta nasıl kaldırılacağını belirleme açıklanmaktadır.
author: adegeo
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1e4a846cf5e3d0209f5ade873520ef64abc12e7c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324654"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>.NET Core çalışma zamanı ve SDK 'sını kaldırma

Zaman içinde, .NET Core çalışma zamanının ve SDK 'sının güncelleştirilmiş sürümlerini yüklerken, eski .NET Core sürümlerini makinenizden kaldırmak isteyebilirsiniz. Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürümü seçiminde](../versions/selection.md)makalesinde açıklandığı gibi, paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma zamanını değiştirebilir.

## <a name="should-i-remove-a-version"></a>Bir sürümü kaldırmalıyım mıyım?

.NET Core [Sürüm seçimi](../versions/selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğu, önceki sürümlerin güvenli şekilde kaldırılmasını mümkün. .NET Core çalışma zamanı güncelleştirmeleri, 1. x ve 2. x gibi ana sürüm ' bantlı ' içinde uyumludur. Ayrıca, .NET Core SDK daha yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturmanıza olanak tanır.

Genel olarak, uygulamanız için gereken çalışma zamanlarının yalnızca en son SDK ve en son düzeltme eki sürümüne ihtiyacınız vardır. Daha eski SDK veya çalışma zamanı sürümlerini tutmak isteyebileceğiniz örnekler, *project.js*tabanlı uygulamalar için koruma içerir. Uygulamanızın önceki SDK 'lar veya çalışma zamanları için belirli nedenleri yoksa, eski sürümleri güvenle kaldırabilirsiniz.

## <a name="determine-what-is-installed"></a>Nelerin yüklendiğini belirleme

.NET Core 2,1 ile başlayarak, .NET CLı, makinenizde yüklü olan SDK ve çalışma zamanının sürümlerini listelemek için kullanabileceğiniz seçeneklere sahiptir.  [`dotnet --list-sdks`](../tools/dotnet.md#options)Makinenizde yüklü SDK 'ların listesini görmek için kullanın. [`dotnet --list-runtimes`](../tools/dotnet.md#options)Makinenizde yüklü olan çalışma zamanlarının listesini görmek için kullanın. Daha fazla bilgi için bkz. [.NET Core 'un zaten yüklü olduğunu denetleme](how-to-detect-installed-versions.md).

## <a name="uninstall-net-core"></a>.NET Core kaldır

::: zone pivot="os-windows"

.NET Core, .NET Core çalışma zamanının ve SDK 'nın sürümlerini kaldırmak için Windows **uygulamaları & özellikleri** iletişim kutusunu kullanır. Aşağıdaki şekilde, **uygulamalar & özellikleri** iletişim kutusu gösterilmektedir. .NET Core 'un yüklü sürümlerini filtrelemek ve göstermek için **Core SDK** araması yapabilirsiniz.

![.NET Core kaldırmak için Program Ekle/Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

Makinenizden kaldırmak istediğiniz herhangi bir sürümü seçip **Kaldır**' a tıklayın.

::: zone-end

::: zone pivot="os-linux"

Linux 'ta .NET Core (SDK veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır. .NET Core ' u kaldırmanın en iyi yolu, .NET Core yüklemek için kullandığınız eylemi yansıtmasıdır. Ayrıntılar, seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.

> [!IMPORTANT]
> Red Hat yüklemeleri için, .NET Core 'u yükleme ve kaldırma hakkında bilgi için, [Red Hat kullanmaya başlama kılavuzuna](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) bakın.

.NET Core 2,1 ' den itibaren, bir paket Yöneticisi kullanılarak yükseltilirken .NET Core SDK kaldırmanız gerekmez. Paket Yöneticisi `update` veya `refresh` komutları, daha yeni bir sürümü başarıyla yüklendikten sonra eski sürümü otomatik olarak kaldırır.

.NET Core 'u bir paket Yöneticisi kullanarak yüklediyseniz, .NET SDK veya çalışma zamanı 'nı kaldırmak için aynı paket yöneticisini kullanın. .NET Core yüklemeleri en popüler paket yöneticilerini destekler. Ortamınızdaki kesin bir sözdizimi için dağıtımın Paket Yöneticisi belgelerine başvurun:

- [apt-get (8)](https://linux.die.net/man/8/apt-get) , Ubuntu dahil olmak üzere, dekim tabanlı sistemler tarafından kullanılır.
- Fedora, CentOS ve Oracle Linux için [yılum (8)](https://linux.die.net/man/8/yum) kullanılır.
- [zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) , openSUSE ve SUSE Linux Enterprise System (SLES) ' de kullanılır.
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) , Fedora 'da kullanılır.

Neredeyse tüm durumlarda, bir paketi kaldırma komutu olur `remove` .

Çoğu paket yöneticisi için .NET Core SDK yüklemesinin paket adı ve `dotnet-sdk` ardından sürüm numarası gelir. Çalışma zamanının .NET Core SDK ve sürümünün sürümü 2.1.300 başlayarak `2.1` , yalnızca büyük ve küçük sürüm numaraları gereklidir: Örneğin, .NET Core SDK sürüm 2.1.300, paket olarak başvurulabilirler `dotnet-sdk-2.1` . Önceki sürümler sürüm dizesinin tamamını gerektirir: Örneğin, `dotnet-sdk-2.1.200` .NET Core SDK sürüm 2.1.200 için gerekli olacaktır.

SDK değil yalnızca çalışma zamanını yükleyen makineler için, paket adı `dotnet-runtime-<version>` .NET Core çalışma zamanına ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığınına yöneliktir.

2,0 ' den önceki .NET Core yüklemeleri, SDK Paket Yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı. Kullanarak `apt-get` , komut şu şekilde olur:

```bash
apt-get remove dotnet-host
```

Uygulamasına iliştirilmiş bir sürüm olmadığını unutmayın `dotnet-host` .

Bir tarbol kullanarak yüklediyseniz, el ile yöntemini kullanarak .NET Core 'u kaldırmanız gerekir.

Linux 'ta, sürümlü dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir. Bunları kaldırmak, SDK ve çalışma zamanını diskten siler. Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

SDK ve çalışma zamanının üst dizinleri, `dotnet --list-sdks` `dotnet --list-runtimes` önceki tabloda gösterildiği gibi, ve komutunun çıktısında listelenir.

::: zone-end

::: zone pivot="os-macos"

Mac üzerinde, sürümlenmiş dizinleri kaldırarak SDK 'Ları ve çalışma zamanlarını ayrı olarak kaldırmanız gerekir. Bunları kaldırmak, SDK ve çalışma zamanını diskten siler. Örneğin, 1.0.1 SDK ve çalışma zamanını kaldırmak için aşağıdaki Bash komutlarını kullanın:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

SDK ve çalışma zamanının üst dizinleri, `dotnet --list-sdks` `dotnet --list-runtimes` önceki tabloda gösterildiği gibi, ve komutunun çıktısında listelenir.

::: zone-end

## <a name="net-core-uninstall-tool"></a>.NET Core Kaldırma Aracı

[.NET Core kaldırma aracı](../additional-tools/uninstall-tool.md) ( `dotnet-core-uninstall` ), bir sistemden .NET Core SDK 'larını ve çalışma zamanlarını kaldırmanıza imkan sağlar. Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>.NET Core SDK sürümlerindeki Visual Studio bağımlılığı

Visual Studio 2019 sürüm 16,3 ' den önce, Visual Studio yükleyicileri tek başına .NET Core SDK yükleyicisini çağırdı. Sonuç olarak, SDK sürümleri Windows **uygulamaları & özellikleri** iletişim kutusunda görünür. Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK 'larını kaldırmak, Visual Studio 'Yu bozabilir. SDK 'Ları kaldırdıktan sonra Visual Studio sorunları varsa, Visual Studio 'nun söz konusu sürümünde Onar ' ı çalıştırın. Aşağıdaki tabloda .NET Core SDK sürümlerindeki bazı Visual Studio bağımlılıkları gösterilmektedir:

| Visual Studio sürüm           | .NET Core SDK sürümü          |
|---------------------------------|--------------------------------|
|  Visual Studio 2019 sürüm 16.2  | .NET Core SDK 2.2.4 xx, 2.1.8 xx |
|  Visual Studio 2019 sürüm 16.1 | .NET Core SDK 2.2.3 xx, 2.1.7 xx |
| Visual Studio 2019 sürüm 16,0 | .NET Core SDK 2.2.2 xx, 2.1.6 xx |
| Visual Studio 2017 sürüm 15,9 | .NET Core SDK 2.2.1 xx, 2.1.5 xx |
| Visual Studio 2017 sürüm 15,8 | .NET Core SDK 2.1.4 xx          |

Visual Studio 2019 sürüm 16,3 ' den itibaren, Visual Studio .NET Core SDK kendi kopyasına göre ücretlendirilir. Bu nedenle, artık bu SDK sürümlerini **uygulamalar & Özellikler** iletişim kutusunda görmezsiniz.

## <a name="remove-the-nuget-fallback-folder"></a>NuGet geri dönüş klasörünü kaldır

.NET Core SDK yükleyicileri, .NET Core 3,0 SDK 'dan önce bir NuGet paketleri önbelleğini depolamak için *Nugetfallbackfolder* adlı bir klasör kullandı. Bu önbellek, veya gibi işlemler sırasında kullanılır `dotnet restore` `dotnet build /t:Restore` . *Nugetfallbackfolder* , Windows üzerinde *C:\Program Files\dotnet\sdk* konumunda ve MacOS 'ta */usr/local/share/DotNet/SDK* konumunda bulunur.

Şu durumlarda bu klasörü kaldırmak isteyebilirsiniz:

- Yalnızca .NET Core 3,0 SDK veya sonraki sürümlerini kullanarak geliştiriyoruz.
- 3,0 'den önceki .NET Core SDK sürümlerini kullanarak geliştiriyoruz, ancak çevrimiçi çalışabilirsiniz.

NuGet geri dönüş klasörünü kaldırmak istiyorsanız, onu silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına sahip olmanız gerekir.

*DotNet* klasörünün silinmesi önerilmez. Bunu yapmak, daha önce yüklediğiniz tüm küresel araçları kaldırır. Ayrıca, Windows üzerinde:

- Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerini bozacaksınız. Kurtarmak için **onarmayı** çalıştırabilirsiniz.
- **Uygulamalar & Özellikler** iletişim kutusunda .NET Core SDK girdileri varsa, bunlar yalnız bırakılmış olacaktır.
