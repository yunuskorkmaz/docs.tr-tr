---
title: ".NET sözlüğü"
description: ".NET belgelerde kullanılan seçili koşulları anlamını öğrenin."
keywords: ".NET sözlüğü, .NET sözlük, .NET terminolojisi, .NET platformu, .NET framework, .NET çalışma zamanı"
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33123732514a53574036f6f8e948b2cf9acb9229
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="net-glossary"></a>.NET sözlüğü

Birincil Bu sözlük anlamları seçili terimleri ve tanımları olmadan .NET belgelerinde sık görünen kısaltmalar açıklamak için hedefidir.

## <a name="aot"></a>AOT

Zaman tamamlanan derleyicisi.

Benzer şekilde [JIT](#jit), bu derleyici ayrıca çevirir [IL](#il) makine kodu. Uygulama yürütülür ve genellikle farklı bir makineye gerçekleştirilen önce JIT derleme aksine, uygulama nesne AĞACI derleme olur. Çalışma zamanında uygulama nesne AĞACI aracı zincirleri derleme yoktur çünkü harcanan süre derleme en aza indirmek yok. Daha fazla zaman iyileştirme harcayabilir anlamına gelir. Uygulama Nesne AĞACI bağlamında tüm uygulama olduğundan, uygulama nesne AĞACI derleyici çapraz modülü bağlama ve tüm başvuruları izlenir ve tek bir yürütülebilir dosya üretilen anlamına gelir tüm program analizi de gerçekleştirir.

## <a name="aspnet"></a>ASP.NET 

.NET Framework ile birlikte gelen özgün ASP.NET uygulaması.

Bazen ASP.NET ASP.NET Core dahil olmak üzere iki ASP.NET uygulamaları başvuran bir genel bir terimdir. Verilen örnek terimi taşıyan anlamı bağlam tarafından belirlenir. Başvurmak için ASP.NET aldığınız temizleyin sağlamak istediğinizde 4.x değil kullanmakta olduğunuz ASP.NET hem uygulamaları anlamına gelir. 

Bkz: [ASP.NET belgelerine](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Core

Bir platformlar arası, yüksek performanslı, açık kaynak uygulaması, ASP .NET Core üzerinde oluşturulmuştur.

Bkz: [ASP.NET Core belgeleri](/aspnet/#pivot=core).

## <a name="assembly"></a>derleme

A *.dll*/*.exe* uygulamaları veya diğer derlemelerden tarafından çağrılabilir API'leri koleksiyonunu içeren dosya.

Bir derlemeyi arabirimleri, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türlerini içerebilir. Bir projenin derlemelerde *bin* klasörü bazen denir *ikili dosyaları*. Ayrıca bkz. [Kitaplığı](#library).

## <a name="clr"></a>CLR

Ortak dil çalışma zamanı.

Bağlama, tam anlamını bağlıdır, ancak bu genellikle .NET Framework çalışma zamanı gösterir. Bellek ayırma ve yönetim CLR işler. CLR ayrıca yalnızca uygulamaları yürütülen ancak aynı zamanda oluşturur ve kod üzerinde-JIT Derleyici kullanarak çalışma sırasında derlenen bir sanal makine bulunuyor. Geçerli Microsoft CLR Windows yalnızca uygulamasıdır.

## <a name="coreclr"></a>CoreCLR

.NET core ortak dil çalışma zamanı.

Bu CLR aynı kod CLR tabanını oluşturulur. İlk olarak, CoreCLR Silverlight'ın çalışma zamanı olan ve birden çok platformda çalışacak biçimde tasarlanan, özellikle Windows ve OS x CoreCLR şimdi parçası .NET Core ve CLR basitleştirilmiş bir sürümünü temsil eder. Bu hala şimdi birçok Linux dağıtımları için destek dahil olmak üzere bir platformlar arası çalışma zamanı gösterir. Ayrıca CoreCLR JIT ve kod yürütme özelliklerine sahip bir sanal makine ' dir.

## <a name="corefx"></a>CoreFX

.NET core temel sınıf kitaplığı (BCL)

Set System.* oluşturan kitaplıkları'nın (ve sınırlı ölçüde Microsoft.*) ad alanları. BCL genel amaçlı, ASP.NET Core gibi daha üst düzey uygulama çerçeveleri derleme üzerinde alt düzey framework olur. .NET Core BCL kaynak kodunu yer [CoreFX depo](https://github.com/dotnet/corefx). Ancak, .NET Core API'ları çoğunluğu kullanılabilir de .NET Framework şekilde CoreFX bir .NET Framework BCL çatalı düşünebilirsiniz.

## <a name="corert"></a>CoreRT

.NET çekirdeği çalışma zamanı.

CLR/CoreCLR aksine CoreRT oluşturmak ve bunu içermediği için kod üzerinde-çalışma sırasında çalıştırmak için kullanılan olanakları içermez anlamına gelen bir sanal makine, değil bir [JIT](#jit). Ancak, içerir [GC](#gc) ve çalışma zamanı tür kimliği (RTTI) ve yansıma yeteneği. Ancak, böylece meta verilerini yansıma için gerekli değildir, tür sistemi tasarlanmıştır. Bu sahip sağlayan bir [Uygulama Nesne AĞACI](#aot) aracı koyma gereksiz meta veri bağlantı ve uygulama kullanmayan kodu (daha da önemlisi) tanımlamak zinciri. CoreRT geliştirme ' dir.

Bkz: [.NET yerel ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="ecosystem"></a>ekosistemi

Tüm çalışma zamanı yazılım, geliştirme araçları ve oluşturmak ve belirli bir teknolojinin uygulamaları çalıştırmak için kullanılan topluluk kaynakları.

".NET ekosistemi" terimi ".NET yığını" gibi benzer terimler, üçüncü taraf uygulamaların ve kitaplıkları, kataloğa farklıdır. Bir tümcedeki örneği şöyledir:

- "Arkasında motivasyon [.NET standart](#net-standard) .NET ekosistemi büyük bütünlüğünü oluşturmaktır." 

## <a name="framework"></a>çerçeve

Genel olarak, geniş kapsamlı bir koleksiyon API'leri, geliştirme ve belirli teknolojiye dayalı uygulamalarının dağıtımını hızlandırır. Bu genel olarak, ASP.NET Core ve Windows Forms uygulama çerçeveleri örnekleridir. Ayrıca bkz. [Kitaplığı](#library).

"Framework" sözcüğünü aşağıdaki terimler içinde daha belirgin bir teknik anlam sahiptir:
* [.NET Framework](#net-framework)
* [hedef çerçevesi](#target-framework)
* [TFM (hedef framework takma ad)](#tfm)

Varolan belgelerde başvurduğu bazen "framework" bir [.NET uygulaması](#implementation-of-net). Örneğin, bir makale bir çerçeve .NET Core çağırabilir. Bu karmaşık kullanım belgelerindeki ortadan planlıyoruz.

## <a name="gc"></a>GC

Çöp toplayıcı.

Çöp toplayıcı otomatik bellek yönetimi uygulamasıdır.  GC artık kullanımda olmayan nesneler tarafından kullanılan belleği serbest bırakır. 

Bkz: [çöp toplama](garbage-collection/index.md).

## <a name="il"></a>IL

Ara dil.

C# gibi daha üst düzey .NET dilleri Ara dile (IL) olarak adlandırılır ve donanım belirsiz yönerge kümesi aşağıya doğru derleyin. IL bazen MSIL (Microsoft IL) veya CIL (ortak IL) olarak adlandırılır.

## <a name="jit"></a>JIT

Yalnızca zaman derleyicisi.

Benzer şekilde [Uygulama Nesne AĞACI](#aot), bu derleyici çevirir [IL](#il) işlemci anlar makine kodu. Uygulama Nesne AĞACI, aksine JIT derleme isteğe bağlı olur ve kodu çalıştırmak için gereken aynı makine üzerinde gerçekleştirilir. JIT derleme uygulama yürütme sırasında oluştuğunda gerçekleştiğinden derleme zamanında çalışma zamanında bir parçasıdır. Bu nedenle, zamanın en iyi duruma getirme kodu ortaya çıkan kodu oluşturmak üzere tasarrufları karşı dengelemek JIT derleyicileri sahip. Ancak bir JIT gerçek donanım bilir ve farklı uygulamaları sevk gerek kalmadan gelen geliştiriciler boş.

## <a name="implementation-of-net"></a>.NET uygulaması

.NET uygulaması aşağıdakileri içerir:

- Bir veya daha fazla çalışma zamanları. Örnekler: CLR, CoreCLR, CoreRT.
- .NET standart sürümü uygular ve ek API'leri içerebilir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçeveleri. Örnekler: ASP.NET, Windows Forms ve WPF .NET Framework dahil edilir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulamalar arasında paylaşılır.

.NET uygulamaları örnekleri:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Evrensel Windows Platformu (UWP)](#uwp)

## <a name="library"></a>kitaplık

Uygulamaları veya diğer kitaplıkları tarafından çağrılabilir API'leri koleksiyonu. Bir veya daha fazla .NET kitaplığı oluşan [derlemeler](#assembly).

Sözcükler kitaplığı ve [framework](#framework) genellikle maliyetle aynı anlamda kullanılır.

## <a name="metapackage"></a>metapackage

Kendi ancak hiçbir kitaplığı olan bir NuGet paketi yalnızca bağımlılıkları bir listesidir. Eklenen paketler isteğe bağlı olarak bir hedef çerçeve için API kurabilirsiniz.

Bkz: [paketleri, Metapackages ve çerçeveleri](../core/packages.md)

## <a name="mono"></a>Mono

Mono küçük bir çalışma zamanı gerekli olduğunda, genel olarak kullanılan bir .NET uygulamasıdır. Bu, Android, Mac, iOS, tvOS ve watchOS Xamarin uygulamalarını çalıştırır ve öncelikle küçük bir yer gerektiren uygulamalar üzerinde odaklanmıştır çalışma zamanı gösterir.

Şu anda yayımlanan .NET standart sürümlerin tümünü destekler.

Geçmişte, Mono büyük API'si .NET Framework'ün uygulanan ve bazı UNIX üzerindeki en popüler özelliklerini benzetilmiş. Bazı durumlarda, bu yetenekleri UNIX Bel .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanı derleyicisi ile kullanılır, ancak ayrıca iOS gibi platformlarda kullanılan bir tam statik derleyici (biri zamanında tamamlanan derleme) sahiptir.

Mono hakkında daha fazla bilgi için bkz: [Mono belgelerine](http://www.mono-project.com/docs/).

## <a name="net"></a>.NET

Şemsiyesi dönem için [.NET standart](#net-standard) ve tüm [.NET uygulamalarında](#implementation-of-net) ve iş yükleri. Her zaman büyük harfle, hiçbir zaman ".Net".

Bkz: [.NET Kılavuzu](index.md)

## <a name="net-core"></a>.NET Core 

.NET platformlar arası, yüksek performanslı, açık kaynaklı uygulamasıdır. Çekirdek ortak dil çalışma zamanı (CoreCLR), çekirdek Uygulama Nesne AĞACI çalışma zamanı (geliştirme, CoreRT), çekirdek temel sınıf kitaplığı ve çekirdek SDK'sı içerir.

Bkz: [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>.NET Core CLI

.NET Core uygulamaları geliştirmek için bir platformlar arası araç zinciri.

Bkz: [.NET Core komut satırı arabirimi (CLI) araçları](../core/tools/index.md).

## <a name="net-core-sdk"></a>.NET Core SDK

Kitaplıkları ve .NET Core uygulamaları ve kitaplıkları oluşturmak geliştiriciler izin araçlar kümesi. İçeren [.NET Core CLI](#net-core-cli) uygulamalar, .NET Core kitaplıkları ve oluşturmaya ve çalıştırmaya uygulamalar ve yürütülebilir dotnet için çalışma zamanı oluşturmak için (*dotnet.exe*), CLI komutları çalıştırır ve uygulamaları çalıştırır.

Bkz: [.NET Core SDK Genel Bakış](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

Yalnızca Windows üzerinde çalışan .NET uygulaması. Ortak dil çalışma zamanı (CLR), temel sınıf kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama framework kitaplıkları içerir.

Bkz: [.NET Framework Kılavuzu](../framework/index.md).

## <a name="net-native"></a>.NET Yerel

Yerel kod tamamlanan-in-time (Uygulama Nesne AĞACI) tam zamanında (JIT) aksine üreten derleyici araç zinciri.

Derleme benzer şekilde Geliştirici makinede C++ derleyicisi ve bağlayıcı works olur. Kullanılmayan kodunu kaldırır ve bu en iyi duruma getirme daha fazla zaman harcayan. Kod kitaplıklarından ayıklar ve bunları yürütülebilir birleştirir. Sonuç tüm uygulamayı temsil eden tek bir modüldür.

UWP .NET yerel tarafından desteklenen ilk uygulama çerçevesi oluştu. Artık, Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekler.

Bkz: [.NET yerel ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Her .NET uygulamasında kullanılabilen .NET API'lerini biçimsel belirtimini.

.NET standart belirtimi, belge kitaplığında adlandırılır. Bir kitaplık API uygulamaları, yalnızca belirtimleri (arabirimler) içerdiğinden .NET standart bir "kitaplığı." çağırmak için yanıltıcı Bu kullanım belgelerindeki dışında .NET standart metapackage adı bağlamında ortadan planlıyoruz (`NETStandard.Library`).

Bkz: [.NET standart](net-standard.md).

## <a name="ngen"></a>NGEN

Yerel (görüntü) oluşturma.

Bu teknoloji kalıcı bir JIT Derleyici düşünebilirsiniz. Genellikle, burada kod yürütülür, ancak derleme genellikle yükleme zamanında oluşuyor makinede kodu derler.

## <a name="package"></a>Paket

Bir NuGet paketi &mdash; veya yeni bir paket &mdash; olan bir *.zip* yazar adı gibi ek meta verilerin yanı sıra aynı ada sahip bir veya daha fazla derlemeler ile dosya.

*.Zip* dosya sahip bir *.nupkg* uzantısı ve varlıkları gibi içerebilir *.dll* dosyaları ve *.xml* dosyaları, birden çok hedef ile kullanmak için çerçeveler ve sürümleri. Bir uygulama veya kitaplığa yüklendiğinde uygun varlıklar uygulama veya kitaplığı tarafından belirtilen hedef çerçevede göre seçilir. Arabirim tanımlayın varlıklar bulunan *ref* klasörü ve uygulama tanımlamak varlıklar olan *lib* klasör.

## <a name="platform"></a>platform

Bir işletim sistemi ve donanım bunu, Windows, macOS, Linux, iOS ve Android gibi çalışır.

Cümle içinde kullanım örnekleri şunlardır:

- ".NET core bir .NET platformlar arası uygulamasıdır." 
- ".NET standart platformuna bağımsızdır ederken Microsoft platformları, PCL profilleri'temsil eder."

.NET belgelerine ".NET platformu" sık kullandığı .NET uygulaması ya da tüm uygulamaları dahil olmak üzere .NET yığını anlamına gelir. Bu kullanımları her ikisi de bu kullanımları belgelerindeki ortadan planlıyoruz birincil (işletim sistemi/donanım) anlamı ile kafası almak eğilimindedir.

## <a name="runtime"></a>çalışma zamanı

Yönetilen bir program yürütme ortamı.

İşletim Sisteminin çalışma zamanı ortamı parçası olan ancak .NET çalışma zamanı parçası değil. .NET çalışma zamanları bazı örnekleri şunlardır:

- Ortak Dil Çalışma Zamanı (CLR)
- Çekirdek ortak dil çalışma zamanı (CoreCLR)
- (UWP için) .NET yerel
- Mono çalışma zamanı

.NET belgelerine bazen "çalışma zamanı".NET uygulaması anlamına için kullanır. Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:

- "Çeşitli .NET çalışma zamanları .NET standart belirli sürümlerini uygulayın."
- "Birden çok çalışma zamanları üzerinde çalıştırmak için tasarlanmıştır kitaplıkları bu framework hedeflemelidir." (.NET standart başvuran)
- ".NET standart belirli sürümlerini çeşitli .NET çalışma zamanları uygulayın. … Her .NET çalışma zamanı sürümü en yüksek .NET standart sürümünü destekler... bildirir."

Bu tutarsız kullanımını ortadan planlıyoruz. 

## <a name="stack"></a>yığın

Birlikte oluşturmak ve uygulamaları çalıştırmak için kullanılan teknolojiler programlama kümesi.

".NET yığını".NET standart ve tüm .NET uygulamaları için anlamına gelir. ".NET yığını" tümceciği için bir .NET uygulaması başvurabilir. 

## <a name="target-framework"></a>hedef çerçevesi

.NET uygulaması veya kitaplık dayanan API'leri koleksiyonu.

Bir uygulama ya da kitaplık .NET Standard (örneğin, .NET standart 2.0), sürüm belirtimi için standartlaştırılmış bir API kümesi tüm .NET uygulamaları arasında olduğu hedefleyebilirsiniz. Bir uygulama ya da kitaplık Ayrıca belirli bir .NET uygulaması sürümü, uygulamaya özel API'leri alır erişimi durumda hedefleyebilirsiniz. Örneğin, Xamarin.iOS hedefleyen bir uygulama erişimi için sağlanan Xamarin iOS API sarmalayıcıları alır.

Kullanılabilir API'ler bir sistemde bir .NET uygulaması yükler derlemeleri tarafından tanımlanan bazı hedef çerçeveyi (örneğin, .NET Framework), hangi uygulama çerçevesi API'leri (örneğin, ASP.NET, WinForms) içerebilir. Paket tabanlı bir hedef çerçeve için (örneğin, .NET standart ve .NET Core), framework API'leri uygulama veya kitaplıkta yüklü paketleri tarafından tanımlanır. Bu durumda, hedef Framework'ü örtük olarak birlikte çerçevesi olun tüm paketler başvuruda bulunan bir metapackage belirtir.

Bkz: [hedef çerçeveler](frameworks.md).

## <a name="tfm"></a>TFM

Hedef framework ad.

Bir .NET uygulaması ya da kitaplık hedef Framework'ü belirtmek için standartlaştırılmış bir belirteci biçimi. Bir hedef çerçeveyi genellikle başvuru kısa bir ad tarafından gibi `net462`. Uzun formlu TFMs (örn. NETFramework, sürüm = 4.6.2) var, ancak genellikle bir hedef Framework'ü belirtmek için kullanılmaz.

Bkz: [hedef çerçeveler](frameworks.md).

## <a name="uwp"></a>UWP

Evrensel Windows platformu.

Windows uygulamaları ve yazılım modern, Dokunmatik özellikli nesnelerin interneti için (IOT) oluşturmak için kullanılan .NET uygulaması. Bu farklı türde hedeflemek isteyebilirsiniz cihazları birleştirmek için PC'ler, tabletler, phablets, telefonlar ve bile Xbox dahil olmak üzere tasarlanmıştır. UWP Merkezi uygulama mağazası, Yürütme Ortamı (Appcontaıner) ve Windows API'larını Win32 yerine kullanılacak bir dizi gibi birçok hizmetler sağlar (WinRT). Uygulamalar, C++, C#, VB.NET ve JavaScript yazılabilir. C# ve VB.NET kullanırken, .NET API'lerini .NET Core tarafından sağlanır.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Kılavuzu](index.md)  
[.NET Framework Kılavuzu](../framework/index.md)  
[.NET Core](../core/index.md)  
[ASP.NET genel bakış](/aspnet/index#pivot=aspnet)  
[ASP.NET çekirdeği genel bakış](/aspnet/index#pivot=core)  

