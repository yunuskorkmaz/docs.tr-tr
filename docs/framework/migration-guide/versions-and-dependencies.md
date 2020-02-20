---
title: Windows işletim sistemi sürümlerini & .NET Framework
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 62ec1e21fd8e95991af6e2f8fa6f99c17249c761
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452727"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework sürümleri ve bağımlılıklar

.NET Framework her sürümü ortak dil çalışma zamanını (CLR), temel sınıf kitaplıklarını ve diğer yönetilen kitaplıkları içerir. Bu makalede sürüme göre .NET Framework temel özellikleri açıklanmakta, temeldeki CLR sürümleri ve ilişkili geliştirme ortamları hakkında bilgi sağlanır ve Windows işletim sistemi (OS) tarafından yüklenen sürümler tanımlanmaktadır.

.NET Framework her yeni sürümü yeni özellikler ekler, ancak önceki sürümlerden özellikleri korur.

CLR kendi sürüm numarası ile tanımlanır. .NET Framework sürüm numarası her sürümde artırılır, ancak CLR sürümü her zaman artmaz. Örneğin, .NET Framework 4, 4,5 ve sonraki sürümlerde CLR 4, .NET Framework 2,0, 3,0 ve 3,5 dahil CLR 2,0 sayılabilir. (CLR'nin sürüm 3'ü yoktur.)

> [!TIP]
>
> - Desteklenen işletim sistemlerinin tüm listesi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).
> - İndirmeler için bkz. [geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md).
> - Bilgisayara hangi .NET Framework sürümlerinin yüklendiğini belirleme hakkında daha fazla bilgi için bkz. [hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Sürüm bilgileri

Aşağıdaki tablolarda, sürüm geçmişi .NET Framework ve her sürümü Visual Studio, Windows ve Windows Server ile ilişkilendirmek özetlenmektedir. Visual Studio çoklu hedefleme destekler, bu nedenle listelenen .NET Framework sürümüyle sınırlı değilsiniz.

- Onay işareti simgesi ✔️, .NET Framework yüklendiği, ancak [Denetim Masası 'nda](../install/dotnet-35-windows-10.md) (Windows için) veya Sunucu Yöneticisi (Windows Server için) etkinleştirilmiş olması gereken işletim sistemi sürümlerini gösterir.
- Artı işareti simgesi ➕, .NET Framework yüklendiği ancak yüklenemeyen işletim sistemi sürümlerini gösterir.

| | |
| - | - |
| [.NET Framework 4,8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4,7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4,6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3,5](#net-framework-35) |
| [.NET Framework 3,0](#net-framework-30) | [.NET Framework 2,0](#net-framework-20) | [.NET Framework 1,1](#net-framework-11) | [.NET Framework 1,0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4,8

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-48)
- [Erişilebilirlik 'de yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Mayıs 2019 güncelleştirmesi<br/>➕ 10 Ekim 2018 Güncelleştirmesi (sürüm 1809)<br/>➕ 10 Nisan 2018 Güncelleştirmesi (sürüm 1803)<br/>➕ 10 Fall Creators Update (sürüm 1709)<br/>➕ 10 Creators Update (sürüm 1703)<br/>➕ 10 yıldönümü Güncelleştirmesi (sürüm 1607)<br/>➕ 8,1<br/>➕ 7|
|**Windows Server sürümleri**|➕ Windows Server 2019<br/>➕ Windows Server, sürüm 1809<br/>➕ Windows Server, sürüm 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br/>-528040 (Windows 10 Mayıs 2019 güncelleştirme)<br/>-528049 (diğer tüm işletim sistemi sürümleri)<br/>(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-472)
- [Erişilebilirlik 'de yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil edilmiştir**|2019<sup>1</sup>|
|**Windows sürümleri**|✔️ 10 Ekim 2018 Güncelleştirmesi (sürüm 1809)<br/>✔️ 10 Nisan 2018 Güncelleştirmesi (sürüm 1803)<br/>➕ 10 Fall Creators Update (sürüm 1709)<br/>➕ 10 Creators Update (sürüm 1703)<br/>➕ 10 yıldönümü Güncelleştirmesi (sürüm 1607)<br/>➕ 8,1<br/>➕ 7|
|**Windows Server sürümleri**|✔️ Windows Server 2019<br/>✔️ Windows Server, sürüm 1809<br/>✔️ Windows Server, sürüm 1803<br/>➕ Windows Server, sürüm 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br/>-461814 (Windows 10 Ekim 2018 güncelleştirmesi)<br/>-461808 (Windows 10 Nisan 2018 güncelleştirme ve Windows Server, sürüm 1803)<br/>-461814 (diğer tüm işletim sistemi sürümleri)<br/>(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> , **.net masaüstü geliştirme**, **ASP.net ve Web geliştirme**, **Azure geliştirme**, **Office/SharePoint geliştirme**, **.NET ile mobil geliştirme**veya **.NET Core platformlar arası geliştirme** iş yükleri yüklemeyi gerektirir.

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-471)
- [Erişilebilirlik 'de yeni](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Fall Creators Update (sürüm 1709)<br/>➕ 10 Creators Update (sürüm 1703)<br/>➕ 10 yıldönümü Güncelleştirmesi (sürüm 1607)<br/>➕ 8,1<br/>➕ 7|
|**Windows Server sürümleri**|➕ Windows Server, sürüm 1803<br/>✔️ Windows Server, sürüm 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br/>-461308 (Windows 10 Creators Update ve Windows Server, sürüm 1709)<br/>-461310 (diğer tüm işletim sistemi sürümleri)<br/>(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-47"></a>.NET framework 4.7

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-47)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 Creators Update (sürüm 1703)<br/>➕ 10 yıldönümü Güncelleştirmesi (sürüm 1607)<br/>➕ 8,1<br/>➕ 7|
|**Windows Server sürümleri**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br/>-460798 (Windows 10 Creators Update)<br/>-460805 (diğer tüm işletim sistemi sürümleri)<br/>(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-462)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|✔️ 10 yıldönümü Güncelleştirmesi (sürüm 1607)<br/>➕ 10 Kasım Güncelleştirmesi (sürüm 1511)<br/>➕ 10<br/>➕ 8,1<br />➕ 7|
|**Windows Server sürümleri**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br /><br/>-394802 (Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016)<br/>-394806 (diğer tüm işletim sistemi sürümleri)<br /><br/>(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-461)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil edilmiştir**|2017<sup>1</sup>|
|**Windows sürümleri**|✔️ 10 Kasım Güncelleştirmesi (sürüm 1511)<br/>➕ 10<br />➕ 8,1<br />➕ 8<br />➕ 7|
|**Windows Server sürümleri**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br /><br/>-394254 (Windows 10 Kasım güncelleştirmesi)<br />-394271 (diğer tüm işletim sistemi sürümleri)<br /><br/>(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> , **.net masaüstü geliştirme**, **ASP.net ve Web geliştirme**, **Azure geliştirme**, **Office/SharePoint geliştirme**, **.NET ile mobil geliştirme**veya **.NET Core platformlar arası geliştirme** iş yükleri yüklemeyi gerektirir.

### <a name="net-framework-46"></a>.NET Framework 4.6

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-2015)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil edilmiştir**|2015|
|**Windows sürümleri**|✔️ 10<br /><br />➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br /><br />-393295 (Windows 10)<br />-393297 (diğer tüm işletim sistemi sürümleri)<br /><br />(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-452)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Windows sürümleri**|➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD 379893 kullanın<br /><br />(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-451)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil edilmiştir**|2013|
|**Windows sürümleri**|✔️ 8,1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD kullanın:<br /><br />-378675 (Windows 8.1)<br />-378758 (tümü)<br /><br />(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Yeni özellikler](../whats-new/index.md#whats-new-in-net-framework-45)
- [Sürüm notları](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil edilmiştir**|2012|
|**Windows sürümleri**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Yüklü .NET sürümünü belirleme**|`Release` DWORD 378389 kullanın<br /><br />(Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-4"></a>.NET Framework 4

[Yeni özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**CLR sürümü**|4|
|**Visual Studio sürümüne dahil edilmiştir**|2010|
|**Windows sürümleri**|➕ 7<br />➕ Vista|
|**Windows Server sürümleri**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003|
|**Yüklü .NET sürümünü belirleme**|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- İfade ağaçları
- AJAX geliştirmesi için iyileştirilmiş ASP.NET desteği
- HashSet koleksiyonları
- DateTimeOffset
- WCF ve WF tümleştirmesi
- Eşler arası ağ oluşturma
- Genişletilebilirlik için eklentiler

|||
|-|-|
|**CLR sürümü**|2,0|
|**Visual Studio sürümüne dahil edilmiştir**|2008|
|**Windows sürümleri**|✔️ 10\*<br/>✔️ 8,1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Windows Server sürümleri**|➕ Windows Server, sürüm 1803\*<br/>➕ Windows Server, sürüm 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️ 2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003|
|**Yüklü .NET sürümünü belirleme**|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|

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
|**Windows Server sürümleri**|✔️ 2008 R2 SP1 *<br />✔️ 2008 SP2\*<br /><br />➕ 2003|
|**Yüklü .NET sürümünü belirleme**|Bkz. [yönergeler](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29):

- Genel Türler
- Hata ayıklayıcı Düzenle ve devam et
- Geliştirilmiş ölçeklenebilirlik ve performans
- ClickOnce dağıtımı
- ASP.NET 2,0 ' de, geniş bir tarayıcı dizisi için yeni denetimler ve destek
- 64-bit desteği

|||
|-|-|
|**CLR sürümü**|2,0|
|**Visual Studio sürümüne dahil edilmiştir**|2005|
|**Windows sürümleri**|YOK|
|**Windows Server sürümleri**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 200|
|**Yüklü .NET sürümünü belirleme**|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Yeni özellikler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29):

- ASP.NET Mobile denetimleri
- Yan yana yürütme
- IPv6 desteği

|||
|-|-|
|**CLR sürümü**|1.1|
|**Visual Studio sürümüne dahil edilmiştir**|2003|
|**Windows sürümleri**|YOK|
|**Windows Server sürümleri**|✔️ 2003|
|**Yüklü .NET sürümünü belirleme**|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**CLR sürümü**|1.0|
|**Visual Studio sürümüne dahil edilmiştir**|Visual Studio .NET|
|**Windows sürümleri**|YOK|
|**Windows Server sürümleri**|YOK|
|**Yüklü .NET sürümünü belirleme**|[Yönergelere](how-to-determine-which-versions-are-installed.md) bakın|

> [!NOTE]
>
> - .NET Framework, bu işletim sisteminde [Denetim Masası (Windows için) veya Sunucu Yöneticisi (Windows Server için)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)üzerinden etkinleştirilmelidir.
> - Genel olarak, kullandığınız bir uygulama belirli bir sürüme bağlı olabileceğinden ve bu sürüm kaldırılırsa kesintiye uğraabileceğinden, bilgisayarınızda yüklü olan .NET Framework sürümlerini kaldırmamalıdır. Birden çok .NET Framework sürümünü aynı anda tek bir bilgisayara yükleyebilirsiniz. Bu, önceki sürümleri kaldırmak zorunda kalmadan .NET Framework yükleyebileceğiniz anlamına gelir. Daha fazla bilgi için bkz [. Başlarken](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Sürüm 4,5 ve üzeri için açıklamalar

.NET Framework 4,5, bilgisayarınızda .NET Framework 4 ' ü değiştiren ve benzer şekilde .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 ve 4,8 .NET Framework 4,5 için yerinde güncelleştirme olan bir yerinde güncelleştirmedir. Yerinde güncelleştirme, aynı çalışma zamanı sürümünü kullandıkları, ancak derleme sürümlerinin güncelleştirilmesi ve yeni türler ve Üyeler içermesi anlamına gelir. Bu güncelleştirmelerden birini yükledikten sonra, .NET Framework 4, .NET Framework 4,5, .NET Framework 4,6 veya .NET Framework 4,7 uygulamalarının yeniden derleme gerekmeden çalışmaya devam etmesi gerekir. Ancak tersi doğru değildir. Daha önceki bir sürümde .NET Framework sonraki bir sürümünü hedefleyen uygulamalar çalıştırmayı önermiyoruz. Örneğin, .NET Framework 4,5 üzerinde 4,6 .NET Framework hedeflerini bir uygulama çalıştırmanızı önermiyoruz.

Aşağıdaki kurallar uygulanır:

- Visual Studio 'da, proje için hedef çerçeve olarak .NET Framework 4,5 ' ı seçebilirsiniz (Bu, <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> özelliğini ayarlar), projeyi bir .NET Framework 4,5 derlemesi veya çalıştırılabilir olarak derlemek için kullanabilirsiniz. Bu derleme veya yürütülebilir dosya .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 yüklü herhangi bir bilgisayarda kullanılabilir.

- Visual Studio 'da, bir projenin .NET Framework 4.5.1 derlemesi veya çalıştırılabilir olarak derlenmesi için hedef Framework olarak .NET Framework 4.5.1 seçebilirsiniz. Bu derlemeyi veya yürütülebilir dosyayı yalnızca .NET Framework 4.5.1 veya üzeri yüklü bilgisayarlarda çalıştırın. .NET Framework 4.5.1 hedefleyen bir yürütülebilir dosyanın yalnızca önceki bir .NET Framework olan .NET Framework 4,5, yüklü bir bilgisayarda çalışması engellenir. Kullanıcıdan .NET Framework 4.5.1 yüklemesi istenir. Ayrıca, .NET Framework 4.5.1 derlemeleri, .NET Framework 4,5 gibi önceki .NET Framework sürümünü hedefleyen bir uygulamadan çağrılmamalıdır.

  > [!NOTE]
  > .NET Framework 4.5.1 ve .NET Framework 4,5 burada yalnızca örnek olarak kullanılır. Açıklanan ilke, üzerinde çalıştığı sistemde yüklü olan .NET Framework sonraki bir sürümünü hedefleyen uygulamalar için geçerlidir.

.NET Framework yapılan bazı değişiklikler, uygulama kodunuzda değişiklik yapılmasını gerektirebilir; Mevcut uygulamalarınızı .NET Framework 4,5 veya sonraki sürümlerle çalıştırmadan önce bkz. [uygulama uyumluluğu](application-compatibility.md) . Geçerli sürümü yükleme hakkında daha fazla bilgi için bkz. [geliştiricilerin .NET Framework yükleme](../install/guide-for-developers.md). .NET Framework için destek hakkında daha fazla bilgi için bkz. .NET Web sitesinde [.NET Framework resmi destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) .

## <a name="remarks-for-older-versions"></a>Eski sürümler için açıklamalar

2,0, 3,0 ve 3,5 .NET Framework sürümleri CLR 'nin aynı sürümüyle (CLR 2,0) oluşturulmuştur. Bu sürümler, tek bir kurulumun ardışık katmanlarını temsil eder. Her sürüm kademeli olarak önceki sürümlerin üzerine yerleştirilir. 2,0, 3,0 ve 3,5 sürümlerini bir bilgisayar üzerinde yan yana çalıştırmak mümkün değildir. Sürüm 3.5'i yüklediğinizde, 2.0 ve 3.0 katmanlarını otomatik olarak alırsınız ve 2.0, 3.0 ve 3.5 sürümleri için oluşturulmuş olan uygulamaların tümü 3.5 sürümü üzerinde çalıştırılabilir. Ancak, .NET Framework 4 Bu katmanlama yaklaşımını sonlandırır ve bu ve sonraki sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 ve 4,8), tek bir yüklemenin birbirini izleyen katmanlarını da temsil eder. .NET Framework 4 ' te başlayarak, tek bir işlemde CLR 'nin birden çok sürümünü çalıştırmak için işlem içi, yan yana barındırma kullanabilirsiniz. Daha fazla bilgi için bkz. [derlemeler ve yan yana yürütme](../../standard/assembly/side-by-side-execution.md).

Ayrıca, uygulamanız 2,0, 3,0 veya 3,5 sürümünü hedefliyorsa, kullanıcılarınız uygulamanızı çalıştırmadan önce Windows 8, Windows 8.1 veya Windows 10 bilgisayarında .NET Framework 3,5 ' i etkinleştirmek zorunda kalabilir. Daha fazla bilgi için bkz. [Windows 10, Windows 8.1 ve Windows 8 ' de .NET Framework 3,5](../install/dotnet-35-windows-10.md)'yi.

## <a name="next-steps"></a>Sonraki adımlar

- .NET Framework yeni başladıysanız, önemli kavramlara ve özelliklere giriş için [genel bakış](../get-started/overview.md) bölümüne bakın.

- .NET Framework 4,5 ve noktası sürümlerindeki yeni özellikler ve geliştirmeler için bkz. [.NET Framework](../whats-new/index.md)yenilikler.

- Uygulamanızı .NET Framework daha yeni bir sürüme geçirme hakkında daha fazla bilgi için, bkz. [Geçiş Kılavuzu](index.md).

- Bir bilgisayarda hangi sürümlerin veya güncelleştirmelerin yüklü olduğunu belirleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md) ve [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini](how-to-determine-which-net-framework-updates-are-installed.md)belirleme.

## <a name="see-also"></a>Ayrıca bkz.

- [Sürüm uyumluluğu](version-compatibility.md)
| [.NET Framework resmi destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)
