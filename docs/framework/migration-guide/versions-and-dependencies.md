---
title: .NET Framework & Windows Işletim Sistemi sürümleri
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504053"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework sürümleri ve bağımlılıkları

.NET Framework'ün her sürümü ortak dil çalışma saatini (CLR), taban sınıf kitaplıklarını ve yönetilen diğer kitaplıkları içerir. Bu makalede, .NET Framework'ün temel özellikleri nin sürümüne göre açıklanır, temel CLR sürümleri ve ilişkili geliştirme ortamları hakkında bilgi sağlar ve Windows işletim sistemi (OS) tarafından yüklenen sürümleri tanımlar.

.NET Framework'ün her yeni sürümü yeni özellikler ekler, ancak önceki sürümlerden özellikleri korur.

CLR kendi sürüm numarası ile tanımlanır. .NET Framework sürüm numarası her sürümde artımlanır, ancak CLR sürümü her zaman artışlı değildir. Örneğin, .NET Framework 4, 4.5 ve sonraki sürümler CLR 4 içerir, ancak .NET Framework 2.0, 3.0 ve 3.5 CLR 2.0 içerir. (CLR'nin sürüm 3'ü yoktur.)

> [!TIP]
>
> - Desteklenen işletim sistemlerinin tam listesi için [Sistem gereksinimlerine](../get-started/system-requirements.md)bakın.
> - İndirmeler için geliştiriciler [için .NET Framework'ü yükleyin'e](../install/guide-for-developers.md)bakın.
> - .NET Framework'ün hangi sürümlerinin bilgisayara yüklendiği hakkında bilgi [için](how-to-determine-which-versions-are-installed.md)bkz.

## <a name="version-information"></a>Sürüm bilgileri

Bunu izleyen tablolar .NET Framework sürüm geçmişini özetler ve her sürümü Visual Studio, Windows ve Windows Server ile ilişkilendirir. Visual Studio çoklu hedeflemeyi destekler, bu nedenle listelenen .NET Framework sürümüyle sınırlı değildir.

- onay işareti simgesi ✔️ .NET Framework yüklü ancak [Denetim Masası](../install/dotnet-35-windows-10.md) (Windows için) veya Server Manager (Windows Server için) aracılığıyla etkinleştirilmesi gereken işletim sistemi sürümlerini gösterir.
- artı işareti simgesi ➕ .NET Framework yüklü gelmiyor ama yüklenebilir işletim sistemi sürümleri gösterir.

| | |
| - | - |
| [.NET Çerçeve 4.8](#net-framework-48) | [.NET Çerçeve 4.7.2](#net-framework-472) | [.NET Çerçeve 4.7.1](#net-framework-471) | [.NET Çerçeve 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a> .NET Framework 4.8

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-48)
- [Erişilebilirlikte yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Mayıs 2019 Güncelleme<br/>➕ 10 Ekim 2018 Güncellemesi (Sürüm 1809)<br/>➕ 10 Nisan 2018 Güncellemesi (Sürüm 1803)<br/>➕ 10 Güz Creators Güncelleme (Sürüm 1709)<br/>➕ 10 Creators Güncellemesi (Sürüm 1703)<br/>➕ 10 Yıldönümü Güncellemesi (Sürüm 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server sürümleri**|➕ Windows Server 2019<br/>➕ Windows Server, sürüm 1809<br/>➕ Windows Server, sürüm 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br/>- 528040 (Windows 10 Mayıs 2019 Güncellemesi)<br/>- 528049 (diğer tüm işletim sistemi sürümleri)<br/>[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-472"></a> .NET Framework 4.7.2

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-472)
- [Erişilebilirlikte yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil**|2019<sup>1</sup>|
|**Windows sürümleri**|✔️ 10 Ekim 2018 Güncellemesi (Sürüm 1809)<br/>✔️ 10 Nisan 2018 Güncellemesi (Sürüm 1803)<br/>➕ 10 Güz Creators Güncelleme (Sürüm 1709)<br/>➕ 10 Creators Güncellemesi (Sürüm 1703)<br/>➕ 10 Yıldönümü Güncellemesi (Sürüm 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server sürümleri**|✔️ Windows Server 2019<br/>✔️ Windows Server, sürüm 1809<br/>✔️ Windows Server, sürüm 1803<br/>➕ Windows Server, sürüm 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br/>- 461814 (Windows 10 Ekim 2018 Güncellemesi)<br/>- 461808 (Windows 10 Nisan 2018 Güncelleme ve Windows Server, sürüm 1803)<br/>- 461814 (diğer tüm işletim sistemi sürümleri)<br/>[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

<sup>1</sup> **.NET masaüstü geliştirme,** **ASP.NET ve web geliştirme,** **Azure geliştirme,** **Office/SharePoint geliştirme,**.NET veya **.NET Core çapraz platform geliştirme** iş yüklerini içeren mobil **geliştirmeyi**yüklemeyi gerektirir.

### <a name="net-framework-471"></a>.NET Çerçeve 4.7.1

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-471)
- [Erişilebilirlikte yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Güz Creators Güncelleme (Sürüm 1709)<br/>➕ 10 Creators Güncellemesi (Sürüm 1703)<br/>➕ 10 Yıldönümü Güncellemesi (Sürüm 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server sürümleri**|➕ Windows Server, sürüm 1803<br/>✔️ Windows Server, sürüm 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br/>- 461308 (Windows 10 Creators Update ve Windows Server, sürüm 1709)<br/>- 461310 (diğer tüm işletim sistemi sürümleri)<br/>[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-47"></a> .NET Framework 4.7

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-47)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Creators Güncellemesi (Sürüm 1703)<br/>➕ 10 Yıldönümü Güncellemesi (Sürüm 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server sürümleri**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (diğer tüm işletim sistemi sürümleri)<br/>[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-462)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Yıldönümü Güncellemesi (Sürüm 1607)<br/>➕ 10 Kasım Güncellemesi (Sürüm 1511)<br/>➕ 10<br/>➕ 8.1<br />➕ 7|
|**Windows Server sürümleri**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br /><br/>- 394802 (Windows 10 Yıldönümü Güncellemesi ve Windows Server 2016)<br/>- 394806 (diğer tüm işletim sistemi sürümleri)<br /><br/>[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-461)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil**|2017<sup>1</sup>|
|**Windows sürümleri**|✔️ 10 Kasım Güncellemesi (Sürüm 1511)<br/>➕ 10<br />➕ 8.1<br />➕ 8<br />➕ 7|
|**Windows Server sürümleri**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br /><br/>- 394254 (Windows 10 Kasım Güncellemesi)<br />- 394271 (diğer tüm işletim sistemi sürümleri)<br /><br/>[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

<sup>1</sup> **.NET masaüstü geliştirme,** **ASP.NET ve web geliştirme,** **Azure geliştirme,** **Office/SharePoint geliştirme,**.NET veya **.NET Core çapraz platform geliştirme** iş yüklerini içeren mobil **geliştirmeyi**yüklemeyi gerektirir.

### <a name="net-framework-46"></a>.NET Framework 4.6

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-2015)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil**|2015|
|**Windows sürümleri**|✔️ 10<br /><br />➕ 8.1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br /><br />- 393295 (Windows 10)<br />- 393297 (diğer tüm işletim sistemi sürümleri)<br /><br />[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-452)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|➕ 8.1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirlemek için**|DWORD 379893 kullanın `Release`<br /><br />[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-451)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil**|2013|
|**Windows sürümleri**|✔️ 8.1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirlemek için**|DWORD kullanın: `Release`<br /><br />- 378675 (Windows 8.1)<br />- 378758 (diğer tüm)<br /><br />[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-45)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil**|2012|
|**Windows sürümleri**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirlemek için**|DWORD 378389 kullanın `Release`<br /><br />[(Talimatlara](how-to-determine-which-versions-are-installed.md)bakın)|

### <a name="net-framework-4"></a>.NET Framework 4

[Yeni özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil**|2010|
|**Windows sürümleri**|➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003|
|**Yüklü .NET sürümünü belirlemek için**|[Talimatlara](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- İfade ağaçları
- AJAX gelişimi için geliştirilmiş ASP.NET desteği
- HashSet koleksiyonları
- DateTimeOffset
- WCF ve WF entegrasyonu
- Eşler Arası ağ
- Genişletilebilirlik için eklentiler

|||
|-|-|
|**CLR sürümü**|2,0|
|**Visual Studio sürümüne dahil**|2008|
|**Windows sürümleri**|✔️ 10\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Windows Server sürümleri**|➕ Windows Server, sürüm 1803\*<br/>➕ Windows Server, sürüm 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003|
|**Yüklü .NET sürümünü belirlemek için**|[Talimatlara](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)):

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**CLR sürümü**|2,0|
|**Windows sürümleri**|✔️ Vista|
|**Windows Server sürümleri**|✔️ 2008 R2 SP1*<br />✔️ 2008 SP2\*<br /><br />➕ 2003|
|**Yüklü .NET sürümünü belirlemek için**|Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29):

- Genel Türler
- Hata ayıklama ve devam
- Geliştirilmiş ölçeklenebilirlik ve performans
- ClickOnce dağıtımı
- ASP.NET 2.0'da, geniş bir tarayıcı dizisi için yeni denetimler ve destek
- 64-bit desteği

|||
|-|-|
|**CLR sürümü**|2,0|
|**Visual Studio sürümüne dahil**|2005|
|**Windows sürümleri**|Yok|
|**Windows Server sürümleri**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 2003|
|**Yüklü .NET sürümünü belirlemek için**|[Talimatlara](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29):

- ASP.NET mobil kontroller
- Yan yana yürütme
- IPv6 desteği

|||
|-|-|
|**CLR sürümü**|1.1|
|**Visual Studio sürümüne dahil**|2003|
|**Windows sürümleri**|Yok|
|**Windows Server sürümleri**|✔️ 2003|
|**Yüklü .NET sürümünü belirlemek için**|[Talimatlara](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**CLR sürümü**|1.0|
|**Visual Studio sürümüne dahil**|Visual Studio .NET|
|**Windows sürümleri**|Yok|
|**Windows Server sürümleri**|Yok|
|**Yüklü .NET sürümünü belirlemek için**|[Talimatlara](how-to-determine-which-versions-are-installed.md) bakın|

> [!NOTE]
>
> - .NET Framework bu işletim sisteminde [Control Panel (Windows için) veya Server Manager (Windows Server için)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)aracılığıyla etkinleştirilmelidir.
> - Genel olarak, .NET Framework'ün bilgisayarınıza yüklenen sürümlerini kaldırmamalısınız, çünkü kullandığınız bir uygulama belirli bir sürüme bağlı olabilir ve bu sürüm kaldırılırsa kırılabilir. .NET Framework'ün birden çok sürümüne aynı anda tek bir bilgisayara yükleyebilirsiniz. Bu, önceki sürümleri kaldırmak zorunda kalmadan .NET Framework yükleyebileceğiniz anlamına gelir. Daha fazla bilgi için [bkz.](../get-started/index.md)

## <a name="remarks-for-version-45-and-later"></a>Sürüm 4.5 ve sonrası için açıklamalar

.NET Framework 4.5, bilgisayarınızdaki .NET Framework 4'ün yerini alan ve benzer şekilde .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.2, 4.7, 4.7.1, 4.7.2 ve 4.8'in yerine gelen bir güncellemedir. Yerinde güncelleştirme, aynı çalışma zamanı sürümünü kullandıkları, ancak derleme sürümlerinin güncelleştirilip yeni türleri ve üyeleri içerdiği anlamına gelir. Bu güncelleştirmelerden birini yükledikten sonra ,NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 veya .NET Framework 4.7 uygulamalarınız yeniden derleme gerektirmeden çalışmaya devam etmelidir. Ancak tersi doğru değildir. .NET Framework'ün daha önceki bir sürümünü hedefleyen uygulamaları önceki bir sürümde çalıştırmanızı önermiyoruz. Örneğin, bir uygulamayı .NET Framework 4.5'te .NET Framework 4.6 hedefleri ile çalıştırmanızı önermiyoruz.

Aşağıdaki kurallar uygulanır:

- Visual Studio'da, .NET Framework 4.5'i bir projenin hedef <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> çerçevesi olarak (bu özelliği ayarlar) seçip projeyi .NET Framework 4.5 derleme veya çalıştırılabilir olarak seçebilirsiniz. Bu derleme veya çalıştırılabilir sonra .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 yüklü olan herhangi bir bilgisayarda kullanılabilir.

- Visual Studio'da ,NET Framework 4.5.1'i bir projenin .NET Framework 4.5.1 derlemesi veya çalıştırılabilir olarak derlemesi için hedef çerçeve olarak seçebilirsiniz. Bu derlemeyi yalnızca .NET Framework 4.5.1 veya daha sonra yüklenmiş bilgisayarlarda çalıştırın. .NET Framework 4.5.1'i hedefleyen bir yürütülebilir, .NET Framework 4.5 gibi .NET Framework 4.5'in daha önceki bir sürümüne sahip bir bilgisayarda çalıştırılması engellenir. Kullanıcıdan .NET Framework 4.5.1'i yüklemesi istenecektir. Ayrıca, .NET Framework 4.5.1 derlemeleri ,NET Framework 4.5 gibi .NET Framework'ün önceki bir sürümünü hedefleyen bir uygulamadan çağrılmamalıdır.

  > [!NOTE]
  > .NET Framework 4.5.1 ve .NET Framework 4.5 burada sadece örnek olarak kullanılmaktadır. Açıklanan ilke, .NET Framework'ün daha sonraki bir sürümünü, üzerinde çalıştığının sisteme yüklenen uygulamadan daha sonraki bir sürümünü hedefleyen herhangi bir uygulama için geçerlidir.

.NET Framework'deki bazı değişiklikler uygulama kodunuzda değişiklik gerektirebilir; mevcut uygulamalarınızı .NET Framework 4.5 veya sonraki sürümlerle çalıştırmadan önce [Uygulama Uyumluluğu'na](application-compatibility.md) bakın. Geçerli sürümü yükleme hakkında daha fazla bilgi için [geliştiriciler için .NET Framework'e yükleyin'e](../install/guide-for-developers.md)bakın. .NET Framework desteği hakkında bilgi için .NET web [sitesindeki .NET Framework resmi destek politikasına](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) bakın.

## <a name="remarks-for-older-versions"></a>Eski sürümler için açıklamalar

.NET Framework sürümleri 2.0, 3.0 ve 3.5 CLR (CLR 2.0) aynı sürümü ile oluşturulur. Bu sürümler, tek bir kurulumun ardışık katmanlarını temsil eder. Her sürüm kademeli olarak önceki sürümlerin üzerine yerleştirilir. Bilgisayarda 2.0, 3.0 ve 3.5 sürümlerini yan yana çalıştırmak mümkün değildir. Sürüm 3.5'i yüklediğinizde, 2.0 ve 3.0 katmanlarını otomatik olarak alırsınız ve 2.0, 3.0 ve 3.5 sürümleri için oluşturulmuş olan uygulamaların tümü 3.5 sürümü üzerinde çalıştırılabilir. Ancak, .NET Framework 4 bu katmanlama yaklaşımını sona erdirer ve daha sonra yayımlar (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.7, 4.7.1, 4.7.2 ve 4.8) de tek bir yüklemenin ardışık katmanlarını temsil eder. .NET Framework 4'ten başlayarak, CLR'nin birden fazla sürümüne tek bir işlemde çalıştırmak için yan yana barındırma işlemini kullanabilirsiniz. Daha fazla bilgi için [Montajlar ve Yan Yana Yürütme'ye](../../standard/assembly/side-by-side-execution.md)bakın.

Ayrıca, uygulamanız sürüm 2.0, 3.0 veya 3.5'i hedefliyorsa, kullanıcılarınızın uygulamanızı çalıştırabilmeleri için önce bir Windows 8, Windows 8.1 veya Windows 10 bilgisayarında .NET Framework 3.5'i etkinleştirmesi gerekebilir. Daha fazla bilgi için windows [10, Windows 8.1 ve Windows 8'de .NET Framework 3.5'i yükleyin.](../install/dotnet-35-windows-10.md)

## <a name="next-steps"></a>Sonraki adımlar

- .NET Framework'de yeniyseniz, temel kavramlara ve özelliklere giriş için [genel bakışa](../get-started/overview.md) bakın.

- .NET Framework 4.5 ve nokta sürümlerindeki yeni özellikler ve geliştirmeler için [.NET Framework'deki yeniliklere](../whats-new/index.md)bakın.

- Uygulamanızı .NET Framework'ün daha yeni bir sürümüne geçirme hakkında bilgi için [geçiş kılavuzuna](index.md)bakın.

- Bilgisayarda hangi sürümlerin veya güncelleştirmelerin yüklü olduğunu belirleme hakkında bilgi için [bkz: Hangi .NET Framework Sürümlerinin Yüklenip](how-to-determine-which-versions-are-installed.md) Yüklenmesini ve [Nasıl Yüklenileni Belirleyin: Hangi .NET Framework Güncelleştirmelerinin Yüklü olduğunu belirleyin.](how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Sürüm uyumluluğu](version-compatibility.md)
| [.NET Framework resmi destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)
