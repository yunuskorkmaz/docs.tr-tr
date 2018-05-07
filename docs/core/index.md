---
title: .NET Core Kılavuzu
description: .NET core bir modüler, yüksek performanslı .NET Windows, Linux ve Mac uygulamaları oluşturmak için uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 7a2548a177f6e62e9c76c336c6e270a139d9fce0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-guide"></a>.NET Core Kılavuzu

> Kullanıma ["Başlarken" öğreticileri](get-started.md) basit bir .NET Core uygulamasının nasıl oluşturulacağını öğrenin. Yalnızca ilk uygulamanızı çalışır almak için birkaç dakika sürer.

.NET core, Microsoft ve .NET topluluğu tarafından korunan bir genel amaçlı geliştirme platformdur [GitHub](https://github.com/dotnet/core). Windows, macOS ve Linux destekleyen platformlar arası ve aygıt, Bulut ve katıştırılmış IOT senaryolarını kullanılabilir. 

En iyi aşağıdaki özelliklere .NET Core tanımlayın:

- **Esnek dağıtım:** uygulamanızda dahil edilebilir veya yan yana kullanıcı - veya makineye yüklenmiş.
- **Platformlar arası:** Windows, macOS ve Linux üzerinde çalışır; diğer işletim sistemleri için bağlantı noktası kurulmuş. [İşletim sistemlerini (OS) desteklenen](https://github.com/dotnet/core/blob/master/roadmap.md), CPU ve uygulama senaryoları büyümesine zaman içinde Microsoft, diğer şirketler ve kişiler tarafından sağlanan.
- **Komut satırı araçları:** tüm ürün senaryoları komut satırında denenmesi. 
- **Uyumlu:** .NET Core, .NET Framework, Xamarin ve Mono, uyumlu aracılığıyla [.NET standart](../standard/net-standard.md).
- **Açık kaynak:** .NET Core platformudur MIT ve Apache 2 lisanslarla açık kaynak. Belge altında lisanslanır [CC tarafından](https://creativecommons.org/licenses/by/4.0/). .NET core olan bir [.NET Foundation](https://dotnetfoundation.org/) projesi.
- **Microsoft tarafından desteklenen:** .NET Core başına Microsoft tarafından desteklenir [.NET çekirdek desteği](https://www.microsoft.com/net/core/support/)

## <a name="composition"></a>Birleşim

.NET core aşağıdaki bölümden oluşur:

- A [.NET çalışma zamanı](https://github.com/dotnet/coreclr), bir tür sistemi, derleme yüklenirken, atık toplayıcı, yerel birlikte çalışabilirliği ve diğer temel hizmetleri sağlar. 
- Bir dizi [framework kitaplıkları](https://github.com/dotnet/corefx), temel veri türleri, uygulama birleşim türleri ve temel yardımcı programlarını sağlar. 
- A [SDK Araçları kümesi](https://github.com/dotnet/cli) ve [dil derleyicileri](https://github.com/dotnet/roslyn) bulunan temel geliştirici deneyimi etkinleştirmek [.NET Core SDK](sdk.md).
- .NET Core uygulamaları başlatmak için kullanılan 'dotnet' uygulama ana bilgisayarı. Çalışma zamanı seçer çalışma zamanı barındırır, bir derlemeyi yükleme ilke sağlar ve uygulamasını başlatır. Aynı ana kadar aynı şekilde SDK Araçları başlatmak için de kullanılır.

### <a name="languages"></a>Diller

C#, Visual Basic ve F # dilleri, uygulamalar ve kitaplıklar için .NET Core yazmak için kullanılabilir. Derleyicileri .NET Core üzerinde .NET Core için herhangi bir yere geliştirmenizi etkinleştirme onu çalışır çalıştırın. Genel olarak, size derleyicileri doğrudan, dolaylı olarak SDK araçları kullanarak ancak kullanmaz.

C#, Visual Basic ve F # derleyicileri ve .NET Core araçları veya çeşitli metin düzenleyiciler ve IDE, Visual Studio dahil olmak üzere tümleşik [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text ve bir seçenek olarak .NET Core geliştirme yapma VIM, Sık kullanılan ortam ve işletim sistemi kodlama. Bu tümleştirme, kısmen iyi çok kişi tarafından sağlanan [OmniSharp proje](http://www.omnisharp.net/).

### <a name="net-apis-and-compatibility"></a>.NET API'ları ve uyumluluk

.NET core, platformlar arası sürümü, .NET Framework temel sınıf kitaplıkları (BCL) katmanında .NET Framework'ün olarak düşünülebilir. Bunu uygulayan [.NET standart](../standard/net-standard.md) belirtimi. .NET core bir alt kümesini .NET Framework veya Mono/Xamarin kullanılabilir API'ler sağlar. Bazı durumlarda, türleri tam olarak uygulanmamıştır (bazı üyeleri kullanılabilir değil veya taşınmış).

Bakmak [.NET Core yol haritası](https://github.com/dotnet/core/blob/master/roadmap.md) .NET Core API yol haritası hakkında daha fazla bilgi edinmek için.

### <a name="relationship-to-net-standard"></a>.NET standart ilişkisi

[.NET standart](../standard/net-standard.md) tutarlı geliştiriciler her .NET uygulamasında bekleyebilirsiniz .NET API'lerini açıklar bir API spec. .NET uygulamaları .NET standart uyumlu kabul edilmesi için ve .NET standardını hedefleyen kitaplıklar desteklemek için bu spec uygulamanız gerekir. 

.NET core .NET standart uygular ve bu nedenle .NET standart kitaplıkları destekler.

### <a name="workloads"></a>İş yükleri

Tek başına, .NET Core Araçlar, yerel Hizmetleri ve metin tabanlı oyunlar için yararlı olan tek bir uygulama modeli--konsol uygulamaları--içerir. Ek uygulama modelleri gibi kendi işlevselliğini genişletmek için .NET Core üzerinde oluşturulmuş:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 Evrensel Windows Platformu (UWP)](https://developer.microsoft.com/windows)
- [UWP hedeflerken Xamarin.Forms](https://www.xamarin.com/forms)

### <a name="open-source"></a>Açık kaynak

[.NET core](https://github.com/dotnet/core) (MIT Lisansı), açık kaynaklı ve katkısı [.NET Foundation](https://dotnetfoundation.org) 2014 Microsoft tarafından. Şimdi en etkin .NET Foundation projelerden biri değil. Bu ücretsiz kişiler ve kişisel, akademik veya ticari amaçlarla dahil olmak üzere şirketler tarafından benimsenmesi. Birden çok şirket uygulamaları, araçları, yeni platformlar ve barındırma hizmetleri bir parçası olarak .NET Core kullanın. Bu şirketler bazıları .NET Core github'da önemli yapmak ve bir parçası olarak ürün yönü üzerine kılavuzluk [.NET Foundation teknik Yönetimi grubu](https://dotnetfoundation.org/blog/tsg-welcome).

## <a name="acquisition"></a>Edinme

.NET core iki ana yolla NuGet.org paketleri ve tek başına dağıtımları olarak dağıtılır.

### <a name="distributions"></a>Dağıtımları

.NET Core adresindeki indirebilirsiniz [.NET Core Başlarken](https://www.microsoft.com/net/core) sayfası.

- *Microsoft .NET Core* dağıtım CoreCLR çalışma zamanı, ilişkili kitaplıkları, bir konsol uygulama ana bilgisayarı içerir ve `dotnet` uygulama Başlatıcısı. Tarafından açıklanan [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) metapackage.
- *Microsoft .NET Core SDK* dağıtım .NET Core ve NuGet paketleri geri yükleniyor ve derleme ve uygulamaları oluşturmak için Araçlar içerir. 

Genellikle, .NET Core geliştirmeye başlamak için .NET Core SDK ilk yüklersiniz. Ek .NET Core (belki de yayın öncesi) derlemeleri yüklemek tercih edebilirsiniz.

### <a name="packages"></a>Paketler

- [.NET core paketleri](packages.md) .NET çekirdeği çalışma zamanı ve kitaplıkları (başvuru derlemeleri ve uygulamalar) içerir. Örneğin, [System.Net.Http](https://www.nuget.org/packages/System.Net.Http/).
- [.NET core Metapackages](packages.md) sürümü tutulan kitaplığı paket uygun kümesini başvurarak çeşitli katmanları ve uygulama modelleri açıklanmaktadır.

## <a name="architecture"></a>Mimari

.NET core bir platformlar arası .NET uygulamasıdır. .NET Core benzersiz birincil mimari endişelere desteklenen platformlar için platforma özel uygulamaları sağlamayı ilişkilidir.

### <a name="environments"></a>Ortamlar

.NET core, Windows, macOS ve Linux Microsoft tarafından desteklenir. Linux üzerinde Microsoft .NET Core Red Hat Enterprise Linux (RHEL) ve Debian dağıtım aileleri çalıştıran birincil olarak destekler.

.NET core şu anda X64 destekler CPU. Windows üzerinde X86 de desteklenir. ARM64 ve ARM32 sürüyor.

[.NET Core yol haritası](https://github.com/dotnet/core/blob/master/roadmap.md) daha ayrıntılı iş yükü ve işletim sistemi ve CPU ortamı destek planları hakkında bilgi sağlar.

Diğer şirketler veya gruplara .NET Core diğer uygulama türleri ve ortam için destekleyebilir.

### <a name="designed-for-adaptability"></a>Uyumluluk için tasarlanmış

.NET core, diğer .NET ürünleri göre çok benzer ancak benzersiz bir ürün olarak oluşturulmuştur. Yeni iş yükleri için ve yeni derleyici toolchains ile yeni platformlar için geniş uyumluluk sağlamak için tasarlanmıştır. Devam eden birkaç işletim sistemi ve CPU bağlantı noktası içeren ve çok daha fazla bilgi için bağlantı noktası kurulmuş. Örnek [LLILC](https://github.com/dotnet/llilc) .NET Core için yerel derleme erken bir prototipini olan proje aracılığıyla [LLVM](http://llvm.org/) derleyici.

Ürün için farklı zamanlamalar yeni platformlarda uyarlanan çeşitli bölümlerini etkinleştirme birkaç parçalara ayrılır. Çalışma zamanı ve platforma özgü temel kitaplıkları bir birim olarak bağlantı noktalı gerekir. Platform belirsiz kitaplıkları olarak çalışmalıdır-yapım tarafından tüm platformlar açıktır. Geliştirici verimliliğini artırmak için bir algoritma veya API uygulanabilir olduğunda platformdan bağımsız C# kodu tercih ederek tam olarak veya bölümü, böylece platform özel uyarlama miktarını azaltarak için bir proje sapması yoktur.

Kişiler genellikle birden çok işletim sistemini desteklemek için .NET Core nasıl uygulandığı isteyin. Genellikle ayrı uygulamaları varsa veya durumunda sorun [koşullu derleme](https://en.wikipedia.org/wiki/Conditional_compilation) kullanılır. Koşullu derleme doğru güçlü sapması ile hem de öyledir.

Büyük çoğunluğu Aşağıda grafikte görebilirsiniz [CoreFX](https://github.com/dotnet/corefx) tüm platformlarda paylaşılan platformdan bağımsız kodudur. Platformdan bağımsız kod tüm platformlarda kullanılan tek bir taşınabilir derleme olarak uygulanabilir.

![CoreFX: Her Platform kodunun satırları](../images/corefx-platforms-loc.png)

Windows ve UNIX benzer boyutta uygulamalarıdır. Windows sahip büyük bir uygulama CoreFX gibi bazı salt Windows özellikleri uygulayan beri [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) ancak henüz yalnızca UNIX kavramları uygulamaz. Ayrıca, Linux ve macOS uygulamaları çoğunluğu paylaşılan UNIX uygulama, Linux ve macOS özel uygulamaları boyutu kabaca benzer durumdayken görürsünüz.


.NET Core platforma özgü ve platformdan bağımsız kitaplıklarında bir karışımını vardır. Birkaç örnek modelinde görebilirsiniz:

- [CoreCLR](https://github.com/dotnet/coreclr) platforma özgüdür. C/C++ oluşturulmuştur, bu nedenle platforma özgüdür yapı tarafından.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) ve [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) depolama ve şifreleme API'leri her işletim sisteminde önemli ölçüde farklı o platforma özgü olan. 
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) ve [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) oluşturmak ve veri yapıları çalışan o platformdan bağımsız olan.

## <a name="comparisons-to-other-net-implementations"></a>Diğer .NET uygulamaları için karşılaştırmaları

Belki de, varolan .NET uygulamalarının karşılaştırarak boyutunu ve .NET Core şeklini anlamanız en kolayıdır. 

### <a name="comparison-with-net-framework"></a>.NET Framework ile karşılaştırma

.NET 2000'de Microsoft tarafından ilk duyurulan ve buradan gelişen. .NET Framework, 15 + yıl aralığı sırasında Microsoft tarafından üretilen birincil .NET uygulaması olmuştur. 

.NET Core ve .NET Framework arasındaki temel farklar: 

- **Uygulama modelleri** --.NET Core desteklemiyor tüm .NET Framework uygulama-modelleri, kısmen çünkü bunların çoğu, WPF (DirectX üstünde yerleşik) gibi Windows teknolojileri oluşturulur. Konsol ve ASP.NET Core app-modelleri .NET Core ve .NET Framework tarafından desteklenir. 
- **API** --.NET Core içeriyor aynı birçoğu, ancak daha az API'leri olarak .NET Framework ve farklı bir şekilde düzenlenmesini (derleme adları farklı; türü şekli anahtar durumlarda değişir). Bu farklılıklar, şu anda genelde .NET Core bağlantı noktası kaynağına yapılan değişiklikler gerektirir. .NET core uygulayan [.NET standart](../standard/net-standard.md) .NET Framework BCL API birkaçını zamanla kapsayacak şekilde büyür API.
- **Alt sistemleri** --.NET Core daha basit uygulama ve programlama modeli amacı ile .NET Framework içinde alt kümesini uygular. Yansıma destekleniyorsa Örneğin, kod erişim güvenliği (CAS), desteklenmiyor.
- **Platformlar** --.NET Framework, Windows ve Windows Server .NET Core macOS ve Linux da desteklerken destekler.
- **Açık kaynaklıdır** --.NET Core açık kaynak olduğu sırada bir [salt okunur alt .NET Framework'ün](https://github.com/microsoft/referencesource) açık bir kaynaktır.

.NET Core benzersizdir ve .NET Framework ve diğer .NET uygulamaları için önemli farklılıklar sahip olsa da, kaynak veya ikili paylaşım teknikleri kullanarak kod paylaşmak basittir. 

### <a name="comparison-with-mono"></a>Mono ile karşılaştırma

[Mono](http://www.mono-project.com/) özgün çapraz platform ve [açık kaynak](https://github.com/mono/mono) ilk 2004'te sevkiyat .NET uygulaması. Bu, .NET Framework'ün topluluk kopya olarak düşünülebilir. Mono proje ekibi Aç dayanıyordu [.NET standartları](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (özellikle ECMA 335) uyumlu bir uygulama sunmak için Microsoft tarafından yayımlanan.

.NET Core ve Mono arasındaki temel farklar:

- **Uygulama modelleri** --Mono .NET Framework uygulama-modelleri (örneğin, Windows Forms) ve bazı ek olanları bir alt kümesini destekler (örneğin, [Xamarin.iOS](https://www.xamarin.com/platform)) Xamarin ürün aracılığıyla. .NET core bunlar desteklemiyor.
- **API** --Mono destekleyen bir [büyük alt](http://docs.go-mono.com/?link=root%3a%2fclasslib) .NET Framework aynı derleme adları kullanarak ve Finansman API'leri.
- **Platformlar** --Mono birçok platformları ve CPU destekler.
- **Açık kaynak** --Mono ile .NET Core MIT lisansı kullanın ve .NET Foundation projeler.
- **Odak** --.NET Core üzerinde bulut iş yüklerini odaklanırken Mono birincil odağı Son yıllarda mobil platformları değil.
