---
title: .NET Framework 'den .NET 5 ' e bağlantı noktası
description: Bir .NET Framework projesi .NET 5 ' e (ve .NET Core 3,1) taşırken yararlı bulabileceğiniz bir işlem taşıma ve bulma araçlarını anlayın.
author: adegeo
ms.date: 03/03/2020
no-loc:
- package.config
- PackageReference
ms.openlocfilehash: 8515689cf4a1be917f12bb8f3315cda89988d773
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605054"
---
# <a name="overview-of-porting-from-net-framework-to-net"></a>.NET Framework .NET 'a taşıma hakkında genel bakış

Bu makalede, kodunuzun .NET Framework .NET 'a (önceki adı .NET Core) taşırken göz önünde bulundurmanız gerekenler hakkında bir genel bakış sunulmaktadır. Birçok proje için .NET Framework .NET 'a taşıma oldukça basittir. Projelerinizin karmaşıklığı proje dosyalarının ilk geçişinden sonra ne kadar iş yapılacağını belirler.

Uygulama modelinin .NET (kitaplıklar, konsol uygulamaları ve Masaüstü uygulamaları gibi) kullanılabildiği projeler genellikle çok az değişiklik gerektirir. Yeni bir uygulama modeli gerektiren projeler (örneğin, ASP.NET ' den ASP.NET Core taşıma gibi), daha fazla iş gerektirir. Eski uygulama modelinden birçok desende dönüştürme sırasında kullanılabilecek eşdeğerleri vardır.

## <a name="unavailable-technologies"></a>Kullanılamayan teknolojiler

.NET Framework .NET 'te bulunmayan bazı teknolojiler vardır:

- [Uygulama etki alanları](net-framework-tech-unavailable.md#application-domains)

  Ek uygulama etki alanlarının oluşturulması desteklenmez. Kod yalıtımı için alternatif olarak ayrı süreçler veya kapsayıcılar kullanın.

- [Uzaktan iletişim](net-framework-tech-unavailable.md#remoting)

  Uzaktan iletişim, uygulama etki alanları arasında iletişim kurmak için kullanılır, artık desteklenmemektedir. İşlemler arasında iletişim için, sınıf veya sınıf gibi uzaktan iletişim (IPC) mekanizmalarını bir alternatif olarak düşünün <xref:System.IO.Pipes> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> .

- [Kod erişim güvenliği (CAS)](net-framework-tech-unavailable.md#code-access-security-cas)

  CAS .NET Framework tarafından desteklenen ancak .NET Framework 4,0 ' de kullanım dışı bırakılmış bir korumalı alana alma tekniğiydi. Güvenlik saydamlığı ile değiştirilmiştir ve .NET 'te desteklenmez. Bunun yerine, işletim sistemi tarafından sunulan sanallaştırma, kapsayıcılar veya Kullanıcı hesapları gibi güvenlik sınırlarını kullanın.

- [Güvenlik saydamlığı](net-framework-tech-unavailable.md#security-transparency)

  CA 'lara benzer şekilde, bu korumalı alana alma tekniği artık .NET Framework uygulamalar için önerilmez ve .NET 'te desteklenmez. Bunun yerine, işletim sistemi tarafından sunulan sanallaştırma, kapsayıcılar veya Kullanıcı hesapları gibi güvenlik sınırlarını kullanın.
  
- <xref:System.EnterpriseServices?displayProperty=fullName>

  <xref:System.EnterpriseServices?displayProperty=fullName> (COM+), .NET sürümünde desteklenmez.

- Windows Workflow Foundation (WF) ve Windows Communication Foundation (WCF)

  WF ve WCF, .NET 5 + ' de (.NET Core dahil) desteklenmez. Alternatifler için bkz. [Corewf](https://github.com/UiPath/corewf) ve [corewcf](https://github.com/CoreWCF/CoreWCF).

Desteklenmeyen bu teknolojiler hakkında daha fazla bilgi için bkz. [.NET Core ve .NET 5 + üzerinde .NET Framework teknolojileri kullanılamıyor](net-framework-tech-unavailable.md).

## <a name="windows-desktop-technologies"></a>Windows Masaüstü teknolojileri

.NET Framework için oluşturulan birçok uygulama Windows Forms veya Windows Presentation Foundation (WPF) gibi bir masaüstü teknolojisini kullanır. Hem Windows Forms hem de WPF .NET 'e eklenmiş, ancak bunlar yalnızca Windows teknolojilerini de sürdürür.

Windows Forms veya WPF uygulamasını geçirmeden önce aşağıdaki bağımlılıkları göz önünde bulundurun:

01. .NET için proje dosyaları .NET Framework farklı bir biçim kullanır.
01. Projeniz .NET 'te kullanılamayan bir API kullanabilir.
01. üçüncü taraf denetimleri ve kitaplıkları .NET 'e eklenmemiş ve yalnızca .NET Framework için kullanılabilir durumda kalmış olabilir.
01. Projeniz artık .NET 'te [kullanılamayan bir teknolojiyi](net-framework-tech-unavailable.md) kullanıyor.

.NET, Windows Forms ve WPF 'nin açık kaynaklı sürümlerini kullanır ve .NET Framework geliştirmeleri içerir.

Masaüstü uygulamanızı .NET 5 ' e geçirmeye yönelik öğreticiler için aşağıdaki makalelerden birine bakın:

- [.NET Framework WPF uygulamalarını .NET 'e geçirme](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [.NET Framework Windows Forms uygulamalarını .NET 'a geçirme](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)

## <a name="windows-specific-apis"></a>Windows 'a özgü API 'Ler

Uygulamalar, .NET tarafından desteklenen platformlardaki yerel kitaplıkları hala P/çağırabilirler. Bu teknoloji Windows ile sınırlı değildir. Ancak, başvuru yaptığınız Kitaplık Windows 'a özgü ise, bir _user32.dll_ veya _kernal32.dll_ gibi, kod yalnızca Windows üzerinde kullanılabilir. Uygulamanızın üzerinde çalışmasını istediğiniz her platform için platforma özgü sürümleri bulmanız ya da kodunuzun tüm platformlarda çalışmak üzere yeterince genel olması gerekir.

Bir uygulamayı .NET Framework 'den .NET 'e taşırken, uygulamanız büyük olasılıkla .NET Framework birlikte dağıtılan bir kitaplığı kullandı. .NET Framework ' de kullanılabilen birçok API, Windows kayıt defteri veya GDI+ çizim modeli gibi Windows 'a özgü teknolojide yer aldığı için .NET 'e eklenmedi.

**Windows Uyumluluk Paketi** , .NET Framework API yüzeyinin büyük bir bölümünü .net 'e sağlar ve [Microsoft. Windows. Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)ile sağlanır.

Daha fazla bilgi için bkz. [.net 'e bağlantı noktası kodu Için Windows Uyumluluk paketini kullanma](windows-compat-pack.md).

## <a name="net-framework-compatibility-mode"></a>Uyumluluk modu .NET Framework

.NET Framework uyumluluk modu .NET Standard 2,0 ' de tanıtılmıştı. Bu uyumluluk modu .NET Standard ve .NET 5 + (ve .NET Core 3,1) projelerinin yalnızca Windows 'daki .NET Framework kitaplıklara başvurmasına olanak tanır. .NET Framework kütüphaneleri, kitaplığın Windows Presentation Foundation (WPF) API 'Leri kullanması gibi tüm projeler için çalışmaz, ancak birçok taşıma senaryosunun engellemesini kaldırabilir. Daha fazla bilgi için, [.NET Framework 'ten .net 'e bağlantı noktası kodu için bağımlılıklarınızı çözümleme](third-party-deps.md#net-framework-compatibility-mode)bölümüne bakın.

## <a name="cross-platform"></a>Platformlar arası

.NET (eski adı .NET Core olarak bilinirdi) platformlar arası olacak şekilde tasarlanmıştır. Kodunuz Windows 'a özgü teknolojilere bağlı değilse, macOS, Linux ve Android gibi diğer platformlarda çalışabilir. Bu, aşağıdaki gibi proje türlerini içerir:

- Kitaplıklar
- Konsol tabanlı araçlar
- Otomasyon
- ASP.NET siteleri

.NET Framework yalnızca Windows bileşenidir. Kodunuz, Windows Forms ve Windows Presentation Foundation (WPF) gibi Windows 'a özgü teknolojileri veya API 'Leri kullandığında, kod yine de .NET üzerinde çalışabilir, ancak diğer işletim sistemlerinde çalışmaz.

Kitaplık veya konsol tabanlı uygulamanızın çok fazla değişiklik yapılmadan platformlar arası kullanılabilmesi mümkündür. .NET ' e taşıma yaparken, bunu göz önünde bulundurmanız ve uygulamanızı diğer platformlarda test etmek isteyebilirsiniz.

## <a name="the-future-of-net-standard"></a>.NET Standard gelecek

[.NET Standard](https://github.com/dotnet/standard) , .NET API 'lerinin çoklu .NET uygulamalarında bulunan resmi bir belirtimidir. .NET Standard arkasındaki mosyon, .NET ekosisteminde daha büyük bir birlik sağlamak idi. .NET 5 ' den itibaren, farklı bir şekilde esneklik oluşturmaya yönelik başka bir yaklaşım benimsemiştir ve bu yeni yaklaşım pek çok senaryoda .NET Standard gereksinimini ortadan kaldırır. Daha fazla bilgi için bkz. [.NET 5 ve .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).

.NET Standard 2,0, .NET Framework desteklemeye yönelik son sürümdür.

## <a name="tools-to-assist-porting"></a>Taşıma yardımcı olmaya yönelik araçlar

Bir uygulamayı .NET Framework el ile .NET 'e taşımak yerine, geçişin bazı yönlerini otomatik hale getirmeye yardımcı olmak için farklı araçlar kullanabilirsiniz. Karmaşık bir projenin, kendi içinde karmaşık bir işlem taşıma işlemidir. Bu araçlar, bu yolculukta yardımcı olabilir.

Uygulamanızın bağlantı noktasına yardım eden bir araç kullanıyor olsanız bile, bu makaledeki [taşıma sırasında dikkat edilecek noktaları](#considerations-when-porting) gözden geçirmeniz gerekir.

### <a name="net-upgrade-assistant"></a>.NET Yükseltme Yardımcısı

[.NET Yükseltme Yardımcısı](upgrade-assistant-overview.md) , farklı türlerde .NET Framework uygulamalarda çalıştırılabilen bir komut satırı aracıdır. .NET Framework uygulamalarını .NET 5 ' e yükseltmeye yardımcı olmak üzere tasarlanmıştır. Araç çalıştırıldıktan sonra, **çoğu durumda uygulama geçişi tamamlamaya daha fazla çaba gerektirir**. Araç, geçişin tamamlanmasına yardımcı olabilecek çözümleyiciler yüklemeyi içerir. Bu araç aşağıdaki .NET Framework uygulamalar türlerinde çalışmaktadır:

- Windows Forms
- WPF
- ASP.NET MVC
- Konsol
- Sınıf kitaplıkları

Bu araç, bu makalede listelenen diğer araçları kullanır ve geçiş işlemini yönlendirir. Araç hakkında daha fazla bilgi için bkz. [.NET Yükseltme Yardımcısı 'Na genel bakış](upgrade-assistant-overview.md).

### <a name="try-convert"></a>dene-Dönüştür

TRY-Convert Aracı, bir projeyi veya tüm çözümü .NET SDK 'sına dönüştürebileceğiniz bir .NET genel aracıdır. Bu bir deyişle, masaüstü uygulamalarını .NET 5 ' e taşıma dahil değildir. Ancak, projenizin özel görevler, hedefler veya içeri aktarmalar gibi karmaşık bir yapı işlemi varsa, bu araç önerilmez.

Daha fazla bilgi için bkz. [TRY-Convert GitHub deposu](https://github.com/dotnet/try-convert).

### <a name="net-portability-analyzer"></a>.NET taşınabilirlik Çözümleyicisi

.NET taşınabilirlik Çözümleyicisi, derlemeleri çözümleyen ve belirtilen hedeflenen .NET platformlarınızda taşınabilir uygulamalar veya kitaplıklar için eksik olan .NET API 'Lerinde ayrıntılı bir rapor sağlayan bir araçtır.

.NET taşınabilirlik Çözümleyicisi 'ni Visual Studio 'da kullanmak için [marketten uzantıyı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)yüklersiniz.

Daha fazla bilgi için bkz. [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md).

### <a name="net-api-analyzer"></a>.NET API Çözümleyicisi

[.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) , çalışma ZAMANıNDA bir API kullanıp kullanmayacağınızı analiz eder <xref:System.PlatformNotSupportedException> . .NET Framework 4.7.2 veya üzeri bir sürümü taşıyorsanız, bu yaygın olmasa da kontrol etmeniz iyidir. .NET üzerinde özel durum oluşturan API 'Ler hakkında daha fazla bilgi için bkz. [.NET Core 'da her zaman özel durum oluşturan API 'ler](../compatibility/unsupported-apis.md).

API Çözümleyicisi, projenize eklediğiniz [Microsoft. DotNet. çözümleyiciler. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/) bir NuGet paketi olarak sunulur.

Daha fazla bilgi için bkz. [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md).

## <a name="considerations-when-porting"></a>Taşıma sırasında dikkat edilecek noktalar

Uygulamanızı .NET 'e taşırken aşağıdaki önerileri sırayla göz önünde bulundurun.

✔️ projelerinizi geçirmek için [.NET Yükseltme Yardımcısı](upgrade-assistant-overview.md) 'Nı kullanmayı düşünün. Bu araç önizlemede olsa da, bu makalede ayrıntılı olarak açıklanan adımları otomatik hale getirir ve geçiş yolunuza devam etmek için harika bir başlangıç noktası sağlar.

✔️ önce bağımlılıklarınızı incelemeyi düşünün. Bağımlılıklarınız .NET 5, .NET Standard veya .NET Core 'u hedeflemelidir.

✔️ bir NuGet _packages.config_ dosyasından [PackageReference](/nuget/consume-packages/package-references-in-project-files) Proje DOSYASıNDAKI ayarlara geçiş yapın. [ _package.config_ Dosyayı dönüştürmek](/nuget/consume-packages/migrate-packages-config-to-package-reference#migration-steps)Için Visual Studio 'yu kullanın.

Uygulamanızı bağlantı noktası oluşturamasanız bile en son proje dosya biçimine yükseltmeyi düşünün ✔️. .NET Framework projeler eski bir proje biçimini kullanır. SDK stilindeki projeler olarak bilinen en son proje biçimi .NET Core ve daha fazlası için oluşturulsa da, .NET Framework ile çalışır. Proje dosyanızın en son biçimde olması, uygulamanızı daha sonra oluşturmak için iyi bir temel sağlar.

✔️ .NET Framework projenizi en az .NET Framework 4.7.2 için yeniden hedefleyebilirsiniz. Bu, .NET Standard var olan API 'Leri desteklemediği durumlarda en son API alternatiflerine yönelik kullanılabilirliği sağlar.

✔️ .NET Core 3,1 yerine .NET 5 ' i hedeflemeyi düşünün. .NET Core 3,1 uzun süreli destek (LTS) altındayken, .NET 5 en son ve .NET 6, yayımlanamadığında LTS olacaktır.

✔️ **Windows Forms ve WPF** projeleri için .NET 5 ' i hedefleyin. .NET 5, masaüstü uygulamalarına yönelik birçok geliştirme içerir.

.NET Framework projeleri ile de kullanılabilecek bir kitaplığı geçiriyorsanız, .NET Standard 2,0 ✔️ hedeflemeyi düşünün. Ayrıca, .NET Framework ve .NET Standard hedefleyerek kitaplığınızı çok hedefleyebilirsiniz.

✔️, [Microsoft. Windows. Compatibility NuGet paketine](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) başvuru ekleme işlemini yaptıktan sonra, eksik API 'lerde hata alırsınız. .NET Framework API yüzeyinin büyük bir bölümü, NuGet paketi aracılığıyla .NET ile kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Yükseltme Yardımcısı 'na genel bakış](upgrade-assistant-overview.md)
- [ASP.NET Core geçişe ASP.NET](/aspnet/core/migration/proper-to-2x)
- [.NET Framework WPF uygulamalarını .NET 'e geçirme](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [.NET Framework Windows Forms uygulamalarını .NET 'a geçirme](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
- [.NET için bağlantı noktası .NET Framework kitaplıkları](libraries.md)
- [.NET 5 vs. Server uygulamaları için .NET Framework](../../standard/choosing-core-framework-server.md)
