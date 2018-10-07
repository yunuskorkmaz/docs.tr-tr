---
title: .NET sözlüğü
description: Seçili koşulları .NET belgelerde kullanılan anlamını öğrenin.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 4ffcf56ba171192048a736b58ddcfa591fd3af58
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840277"
---
# <a name="net-glossary"></a>.NET sözlüğü

Bu sözlük birincil amacı, seçili terimleri ve tanımları olmadan .NET belgeleri sık görünen kısaltmalar anlamları açıklamak sağlamaktır.

## <a name="aot"></a>AOT

Derleyici, zaman üretim.

Benzer şekilde [JIT](#jit), ayrıca bu derleyici çevirir [IL](#il) makine kodu. Uygulama çalıştırılır ve genellikle farklı bir makinede gerçekleştirdiği önce JIT derlemesi aksine AOT derlemesi'olmuyor. Çalışma zamanında AOT takımlarına derlenmemesi çünkü derleme harcanan zamanı en aza indirmek yok. Daha fazla iyileştirme zaman harcamak anlamına gelir. AOT bağlamında tüm uygulama olduğundan, AOT derleyici zakazuje optimalizaci bağlama ve tüm başvurular izlenir ve tek bir yürütülebilir dosya oluşturulur ve tüm program analizi de gerçekleştirir.

## <a name="aspnet"></a>ASP.NET 

.NET Framework ile birlikte gelen özgün ASP.NET uygulaması.

Bazen ASP.NET, ASP.NET Core dahil olmak üzere iki ASP.NET uygulamaları için başvuran bir genel bir terimdir. Belirtilen örnek terimi taşıyan anlamı bağlam tarafından belirlenir. Başvurmak için ASP.NET 4.x, Temizle sağlamak istediğinizde değil kullanmakta olduğunuz ASP.NET hem de uygulamaları auto'yu. 

Bkz: [ASP.NET belgeleri](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Platformlar arası, yüksek performanslı, açık kaynaklı bir ASP.NET uygulaması üzerinde .NET Core üzerine kurulmuştur.

Bkz: [ASP.NET Core belgeleri](/aspnet/#pivot=core).

## <a name="assembly"></a>derleme

A *.dll*/*.exe* API uygulamaları veya diğer derlemeler tarafından çağrılabilen bir koleksiyonunu içeren dosya.

Bir bütünleştirilmiş kod arabirimleri, sınıflar, yapılar, sabit listeleri ve temsilciler gibi türlerini içerebilir. Projenin derlemelerini *bin* klasör bazen denir *ikili dosyaları*. Ayrıca bkz: [Kitaplığı](#library).

## <a name="clr"></a>CLR

Ortak dil çalışma zamanı.

Tam anlamı bağlam üzerinde bağlıdır, ancak bu genellikle .NET Framework çalışma zamanını gösterir. CLR bellek ayırma ve management işler. CLR ayrıca yalnızca uygulamaları yürütür, ancak ayrıca oluşturur ve kod üzerinde kolayca kullanarak derler bir sanal makine olduğu bir [JIT](#jit) derleyici. Geçerli Microsoft CLR Windows yalnızca uygulamasıdır.

## <a name="coreclr"></a>CoreCLR

.NET core ortak dil çalışma zamanı.

Bu CLR aynı kod tabanını CLR oluşturulur. İlk olarak, CoreCLR Silverlight çalışma zamanı olan ve birden çok platformda çalışacak şekilde tasarlanmıştır, özellikle Windows ve OS x CoreCLR, artık .NET Core parçasıdır ve Basitleştirilmiş bir CLR sürümünü temsil eder. Hala bir [platformlar arası](#cross-platform) artık çok sayıda Linux dağıtımları da dahil olmak üzere çalışma zamanı. CoreCLR, ayrıca bir sanal makine JIT ve kod yürütme özelliklere sahip olur.

## <a name="corefx"></a>CoreFX

.NET core temel sınıf kitaplığı (BCL)

Kümesini oluşturan System.* kitaplıkları (ve sınırlı bir ölçüde Microsoft.*) ad alanları. Genel amaçlı, ASP.NET Core gibi daha üst düzey uygulama çerçeveleri yapı üzerinde düşük düzeyli framework BCL olur. .NET Core BCL kaynak kodunu bulunan [Corefx'te depo](https://github.com/dotnet/corefx). Ancak, .NET Core API'ları çoğunu de mevcuttur .NET Framework şekilde Corefx'te .NET Framework BCL çatal olarak düşünebilirsiniz.

## <a name="corert"></a>CoreRT

.NET core çalışma zamanı.

CLR/CoreCLR aksine CoreRT oluşturmak ve bunu içermez çünkü kod üzerinde kolayca çalıştırmak için özellikleri içermez anlamına gelir. bir sanal makine, değil bir [JIT](#jit). Ancak, dahil [GC](#gc) ve çalışma zamanı türü tanımı (RTTI) ve yansıma olanağı. Böylece meta verilerini yansıma için gerekli değildir, ancak kendi tür sistemi tasarlanmıştır. Böylece sahip bir [AOT](#aot) aracının koyma gereksiz meta verileri bağlama ve uygulama kullanmayan kod (daha da önemlisi) tanımlamak zinciri. CoreRT geliştirme aşamasında olan.

Bkz: [.NET Native ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="cross-platform"></a>platformlar arası

Geliştirin ve Linux, Windows ve iOS gibi birden çok farklı işletim sistemlerinde özellikle her biri için yeniden yazmak zorunda kalmadan kullanılabilir bir uygulama yürüttüklerinde yeteneği. Bu kod yeniden kullanımı ve farklı platformlarda uygulamalar arasında tutarlılık sağlar.

## <a name="ecosystem"></a>ekosistemi

Tüm çalışma zamanı yazılım, geliştirme araçlarını ve topluluk kaynakları, derlemek ve çalıştırmak için belirli bir teknoloji uygulamalar için kullanılır.

".NET ekosisteminin" terimi benzer terimleri ".NET yığını" gibi üçüncü taraf uygulamaları ve kitaplıkları edilme farklıdır. Bir tümcedeki bir örnek aşağıdadır:

- "Hacktivism arkasında [.NET Standard](#net-standard) .NET ekosisteminde büyük gerekmemesi oluşturmaktır." 

## <a name="framework"></a>çerçeve

Genel olarak, kapsamlı bir API koleksiyonudur, geliştirme ve belirli teknolojiye dayalı uygulamaların dağıtımı kolaylaştırır. Bu genel olarak, ASP.NET Core ve Windows Forms uygulama çerçeveleri örnekleridir. Ayrıca bkz: [Kitaplığı](#library).

"Framework" sözcüğü aşağıdaki koşulları'nda daha ayrıntılı bir teknik anlamı:
* [.NET Framework](#net-framework)
* [Hedef Çerçeve](#target-framework)
* [TFM (hedef çerçeve adı)](#tfm)

Mevcut belgelerde başvurduğu bazen "framework" bir [.NET uygulaması](#implementation-of-net). Örneğin, bir makale, bir çerçeve .NET Core çağırabilir. Bu karmaşık kullanım belgelerinden ortadan kaldırmayı planlıyoruz.

## <a name="gc"></a>GC

Çöp toplayıcı.

Çöp toplayıcı otomatik bellek yönetimi uygulamasıdır.  GC artık kullanımda olmayan nesneler tarafından kapladığı bellek serbest bırakır. 

Bkz: [çöp toplama](garbage-collection/index.md).

## <a name="il"></a>IL

Ara dili.

C# gibi daha üst düzey .NET dilleri Ara dil (IL) olarak adlandırılır ve Donanım sorun yaşamaz yönerge kümesi aşağı derleyin. IL bazen MSIL (Microsoft IL) veya CIL (ortak IL) adlandırılır.

## <a name="jit"></a>JIT

Tam zamanında derleyici.

Benzer şekilde [AOT](#aot), bu derleyici çevirir [IL](#il) işlemci anlayan bir makine kodu. AOT, aksine JIT derlemesi isteğe bağlı olur ve kodu çalıştırmak için gereken aynı makineye gerçekleştirilir. JIT derlemesi uygulamanın yürütülmesi sırasında gerçekleşir olduğundan, derleme zamanında bir parçasıdır. Bu nedenle, JIT derleyicileri harcanan zamanı en iyi duruma getirme kodu elde edilen kod üretebilirsiniz tasarruf karşı dengelemeniz gerekir. Ancak bir JIT gerçek donanım bilir ve farklı uygulamalar gönderin zorunda geliştiriciler boşaltabilir.

## <a name="implementation-of-net"></a>.NET uygulaması

.NET uygulaması şunları içerir:

- Bir veya daha fazla çalışma zamanları. Örnekler: CLR, CoreCLR CoreRT.
- .NET Standard'ın bir sürümünü uygular ve ek API'ler dahil edebilirsiniz bir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçeveleri. Örnekler: ASP.NET, Windows Forms ve WPF .NET Framework dahil edilir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları, birden çok uygulama arasında paylaşılır.

.NET uygulamaları örnekleri:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Evrensel Windows Platformu (UWP)](#uwp)

## <a name="library"></a>kitaplık

Uygulamaları veya diğer kitaplıkları tarafından çağrılabilen bir API koleksiyonudur. Bir veya daha fazla .NET kitaplığı oluşur [derlemeleri](#assembly).

Sözcükleri kitaplığı ve [framework](#framework) genellikle maliyetle aynı anlamda kullanılır.

## <a name="metapackage"></a>metapackage

Kendi ancak hiçbir kitaplığı olan bir NuGet paketi yalnızca bağımlılıkları bir listesidir. Eklenen paketler, isteğe bağlı olarak bir hedef çerçeve için API bağlantı kurabilir.

Bkz: [paketler, meta paketler ve çerçeveler](../core/packages.md)

## <a name="mono"></a>Mono

Mono, bir açık kaynak [platformlar arası](#cross-platform) küçük bir çalışma zamanı gerektiğinde .NET uygulamasında, esas olarak kullanılır. Bu, Android, Mac, iOS, tvOS ve watchOS Xamarin uygulamalarını çalıştırır ve öncelikli olarak küçük ayak izine gerektiren uygulamaları üzerinde odaklanmıştır çalışma zamanıdır.

Tüm şu anda yayımlanan .NET Standard sürümlerini destekler.

Tarihsel olarak, Mono .NET Framework'ün daha büyük API uygulanan ve bazı UNIX üzerinde en popüler özelliklerini benzetilmiş. Bazen UNIX bu özellikleri kullanan .NET uygulamaları çalıştırmak için kullanılır.

Mono genellikle bir tam zamanında derleyici ile kullanılır, ancak ayrıca iOS gibi platformlarda kullanılan tam statik bir derleyici (, zamanında tamamlanan derleme) sahiptir.

Mono hakkında daha fazla bilgi için bkz: [Mono belgeleri](https://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Genel terimi [.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri. Her zaman büyük harfe, hiçbir zaman ".Net".

Bkz: [.NET Kılavuzu](index.md)

## <a name="net-core"></a>.NET Core 

.NET bir platformlar arası, yüksek performanslı, açık kaynak uygulaması. Çekirdek ortak dil çalışma zamanı (CoreCLR), çekirdek AOT çalışma zamanı'nı (geliştirme, CoreRT), çekirdek temel sınıf kitaplığı ve Core SDK'sı içerir.

Bkz: [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>.NET core CLI

.NET Core uygulamaları geliştirmek için bir çoklu platform araç zinciri.

Bkz: [.NET Core komut satırı arabirimi (CLI) araçlarını](../core/tools/index.md).

## <a name="net-core-sdk"></a>.NET core SDK'sı

Kitaplıklar ve geliştiricilerin, .NET Core uygulamaları ve kitaplıkları oluşturmak araçlar kümesi. İçerir [.NET Core CLI](#net-core-cli) uygulamaları, .NET Core kitaplıkları ve oluşturmak ve çalışan uygulamalar ve dotnet yürütülebilir için çalışma zamanı oluşturmak için (*dotnet.exe*) CLI komutları çalıştırır ve uygulamaları çalıştırır.

Bkz: [.NET Core SDK'ya genel bakış](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Yalnızca Windows üzerinde çalışan .NET uygulaması. Ortak dil çalışma zamanı (CLR), temel sınıf kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama framework kitaplıkları içerir.

Bkz: [.NET Framework Kılavuzu](../framework/index.md).

## <a name="net-native"></a>.NET Yerel

Yerel kod tamamlanan-'ın-time (AOT), just-in-time (JIT) aksine üretir derleyici araç zinciri.

Derleme, bir C++ Derleyici ve bağlayıcı çalıştığı benzer şekilde Geliştirici makinesinde gerçekleşir. Kullanılmayan kod kaldırır ve iyileştirmeye daha fazla zaman harcadığını. Bu kod kitaplıklarından ayıklar ve yürütülebilir dosyada birleştirir. Sonuç, tüm uygulamayı temsil eden tek bir modüldür.

UWP .NET Native tarafından desteklenen ilk uygulama çerçevesi oluştu. Şimdi, Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekler.

Bkz: [.NET Native ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET standard

Bir resmi belirtimi .NET API'leri, her bir .NET uygulamasında kullanılabilir.

.NET Standard belirtimi, belge kitaplığında adlandırılır. API uygulamaları, yalnızca belirtimleri (arabirimleri), bir kitaplık içerdiği için "kitaplık.".NET Standard çağrılacak yanıltıcı .NET Standard metapackage adını yalnızca söz konusu kullanım için belgelerinde dışında ortadan kaldırmak planlıyoruz (`NETStandard.Library`).

Bkz: [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Yerel (görüntü) oluşturma.

Bu teknoloji kalıcı bir JIT derleyicisi düşünebilirsiniz. Genellikle, burada kod yürütülür, ancak derleme, genellikle yükleme zamanında oluşuyor makine kodu derler.

## <a name="package"></a>Paket

Bir NuGet paketi &mdash; veya yalnızca bir paketi &mdash; olduğu bir *.zip* dosyasıyla birlikte ek meta verileri yazar adı gibi aynı ada sahip bir veya daha fazla derlemeleri.

*.Zip* dosyasının bir *.nupkg* uzantısı ve varlıklar gibi içerebilir *.dll* dosyaları ve *.xml* dosyaları, birden çok hedef ile kullanmak için çerçeveler ve sürümleri. Bir uygulama veya kitaplık yüklendiğinde, uygulama veya kitaplık tarafından belirtilen hedef Framework'ü temel uygun varlıkları seçilir. Arabirim tanımlayan varlıkları bulunan *ref* klasörü ve uygulanması tanımlamak varlıkları bulunduğunuz *LIB* klasör.

## <a name="platform"></a>platform

Bir işletim sistemi ve Windows, macOS, Linux, iOS ve Android gibi üzerinde çalıştığı donanım.

Cümleleri kullanımı örnekleri aşağıda verilmiştir:

- ".NET core bir çoklu platform .NET uygulamasıdır." 
- ".NET Standard platformu belirsiz modundayken PCL profilleri Microsoft platformları gösterir."

.NET belgeleri ".NET platformu" sık kullandığı .NET uygulaması ya da dahil tüm uygulamaları .NET yığını auto'yu. Bu kullanımları belgelerinden ortadan kaldırmak planlıyoruz için birincil (işletim sistemi/donanım) anlamı kafanız almak için bu kullanımları her ikisi de eğilimindedir.

## <a name="runtime"></a>çalışma zamanı

Yönetilen bir program yürütme ortamı.

İşletim Sisteminin çalışma zamanı ortamının parçası olan ancak .NET çalışma zamanı bir parçası değil. .NET çalışma zamanları bazı örnekleri aşağıda verilmiştir:

- Ortak Dil Çalışma Zamanı (CLR)
- Çekirdek ortak dil çalışma zamanı (CoreCLR)
- (UWP için) .NET native
- Mono çalışma zamanı

.NET belgeleri bazen "çalışma zamanı".NET uygulaması birlikte kullanıldığı senaryolar için kullanır. Örneğin, aşağıdaki cümlelerde, "uygulama" ile "çalışma zamanı" değiştirilmelidir:

- "Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygulayın."
- "Birden çok çalışma zamanları üzerinde çalışması amaçlanmıştır kitaplıkları bu framework hedeflemesi gereken." (.NET Standard başvuran)
- ".NET Standard belirli sürümlerini çeşitli .NET çalışma zamanları uygulayın. … Her .NET çalışma zamanı sürümünü destekleyen... en yüksek .NET Standard sürümünü bildirir."

Bu tutarsız kullanım ortadan kaldırmayı planlıyoruz. 

## <a name="stack"></a>yığın

Programlama birlikte oluşturmak ve uygulamaları çalıştırmak için kullanılan teknolojileri kümesi.

".NET yığını".NET Standard ve tüm .NET uygulamaları için ifade eder. ".NET yığını" tümceciği için bir .NET uygulaması başvurabilir. 

## <a name="target-framework"></a>Hedef Çerçeve

.NET uygulama veya kitaplık dayanan bir API koleksiyonudur.

Bir uygulama veya kitaplık belirtimi için standartlaştırılmış bir API kümesi genelinde tüm .NET uygulamalarında olduğu (örneğin, .NET Standard 2.0), .NET Standard'ın bir sürümünü hedefleyebilirsiniz. Bir uygulama veya kitaplık Ayrıca belirli bir .NET uygulaması sürümü, uygulamaya özel API'lerine erişimi alır durumda hedefleyebilirsiniz. Örneğin, Xamarin.iOS hedefleyen bir uygulama erişimi için sağlanan Xamarin iOS API sarmalayıcıları alır.

Kullanılabilir API'ler, bir .NET uygulamasını yükleyen bir sistemde derlemeler tarafından tanımlanan bazı hedef çerçeveleri için (örneğin, .NET Framework), uygulama çerçevesi API'leri (örneğin, ASP.NET, WinForms) içerebilir. (Örneğin, .NET Standard ve .NET Core) paket tabanlı hedef çerçeve için framework API uygulama veya kitaplık yüklü paketleri tarafından tanımlanır. Bu durumda, hedef Framework'ü örtük olarak birlikte framework yaptığınız tüm paketleri başvuran bir metapackage belirtir.

Bkz: [hedef çerçeveyi](frameworks.md).

## <a name="tfm"></a>TFM

Hedef Çerçeve adı.

Bir .NET uygulaması veya kitaplığı hedef Framework'ü belirtmek için standartlaştırılmış bir belirteci biçimi. Hedef Çerçeve genellikle başvuru kısa bir ad tarafından gibi `net462`. Uzun biçimli Tfm'ler (örn. NETFramework, sürüm 4.6.2 =) var, ancak genellikle bir hedef Framework'ü belirtmek için kullanılmaz.

Bkz: [hedef çerçeveyi](frameworks.md).

## <a name="uwp"></a>UWP

Evrensel Windows platformu.

Windows uygulamaları ve yazılım modern ve Dokunmatik kullanıma nesnelerin interneti için (IOT) oluşturmak için kullanılan bir .NET uygulaması. Bunu hedeflemek isteyebilirsiniz cihazlar farklı türde buluşturulan PC'ler, tabletler, phablets, telefonlar ve bile Xbox dahil olmak üzere tasarlanmıştır. UWP, merkezi bir mağazaya, Yürütme Ortamı (AppContainer) ve bir dizi yerine Win32 kullanmak için Windows API gibi birçok hizmetleri sunar (WinRT). Uygulamaları, C++, C#, VB.NET ve JavaScript içinde yazılabilir. C# ve vb.NET'TE kullanırken, .NET API'lerini .NET Core tarafından sağlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Kılavuzu](index.md)  
- [.NET Framework Kılavuzu](../framework/index.md)  
- [.NET Core](../core/index.md)  
- [ASP.NET genel bakış](/aspnet/index#pivot=aspnet)  
- [ASP.NET Core genel bakış](/aspnet/index#pivot=core)  
