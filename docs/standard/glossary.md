---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili terimlerin anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 8da1d858835210590a80a624fb8989fbfe8e0a91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400437"
---
# <a name="net-glossary"></a>.NET Sözlüğü

Bu sözlüğün birincil amacı, .NET belgelerinde tanımları olmadan sık sık görünen seçili terimlerin ve kısaltmaların anlamlarını netleştirmektir.

## <a name="aot"></a>AOT

Zaman compiler'ı.

[JIT](#jit)benzer, bu derleyici de makine kodu [IL](#il) çevirir. JIT derlemesinin aksine, AOT derlemesi uygulama yürütülmeden önce gerçekleşir ve genellikle farklı bir makinede gerçekleştirilir. AOT takım zincirleri çalışma zamanında derlenmediği için derleme için harcanan zamanı en aza indirmek zorunda değildir. Bu da optimizasyon için daha fazla zaman harcayabilecekleri anlamına gelir. AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi ayrıca tüm başvuruların takip edildiği ve tek bir çalıştırılabilir üretildiği anlamına gelen çapraz modül bağlantı ve tam program analizi ni gerçekleştirir.

[Bkz. CoreRT](#corert) ve [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

.NET Framework ile yapılan orijinal ASP.NET uygulaması.

Bazen ASP.NET, ASP.NET Core dahil olmak üzere her iki ASP.NET uygulamaları ifade eden bir şemsiye terimdir. Terimin herhangi bir durumda taşıdığı anlam bağlam tarafından belirlenir. Her iki uygulama anlamına ASP.NET kullanmadığınızı açıkça belirtmek istediğinizde ASP.NET 4.x'e bakın.

[ASP.NET dokümantasyona](/aspnet/#pivot=aspnet)bakın.

## <a name="aspnet-core"></a>ASP.NET Çekirdeği

.NET Core üzerine inşa edilmiş ASP.NET çapraz platform, yüksek performanslı, açık kaynak uygulaması.

[Bkz. ASP.NET Çekirdek belgeleri.](/aspnet/#pivot=core)

## <a name="assembly"></a>derleme

Uygulamalar veya diğer derlemeler tarafından çağrılabilen bir API koleksiyonu içerebilen *.dll*/*.exe* dosyası.

Derleme, arabirimler, sınıflar, yapılar, sayısallamalar ve temsilciler gibi türleri içerebilir. Projenin *çöp kutusu* klasöründeki derlemeler bazen *ikili*olarak adlandırılır. Ayrıca [kitaplık](#library)bakın.

## <a name="clr"></a>CLR

Ortak Dil Çalışma Zamanı.

Tam anlamı içeriğe bağlıdır, ancak bu genellikle .NET Framework çalışma zamanı anlamına gelir. CLR bellek ayırma ve yönetimi işler. CLR aynı zamanda sadece uygulamaları yürütmekle kalmamış, aynı zamanda [bir JIT](#jit) derleyicisi kullanarak anında kod üreten ve derleyen sanal bir makinedir. Geçerli Microsoft CLR uygulaması yalnızca Windows'dur.

## <a name="coreclr"></a>CoreCLR

.NET Çekirdek Ortak Dil Çalışma Zamanı.

Bu CLR, CLR ile aynı kod tabanından oluşturulmuştür. Başlangıçta, CoreCLR Silverlight çalışma zamanı ve birden fazla platformda çalıştırmak için tasarlanmıştır, özellikle Windows ve OS X. CoreCLR şimdi .NET Core bir parçasıdır ve CLR basitleştirilmiş bir sürümünü temsil eder. Hala birçok Linux dağıtımı için destek de dahil olmak üzere, bir [çapraz platform](#cross-platform) çalışma zamanı. CoreCLR aynı zamanda JIT ve kod yürütme yetenekleri ile sanal bir makinedir.

## <a name="corefx"></a>CoreFX

.NET Çekirdek Taban Sınıf Kitaplığı (BCL)

Sistemi oluşturan bir dizi kitaplık. \* (ve sınırlı bir ölçüde\*Microsoft. ) ad boşlukları. BCL, ASP.NET Core gibi üst düzey uygulama çerçevelerinin temeline sahip olan genel bir amaç, alt düzey bir çerçevedir. .NET Core BCL'nin kaynak kodu [.NET Core çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur. Ancak, .NET Core API'lerinin çoğu .NET Framework'de de mevcuttur, böylece CoreFX'i .NET Framework BCL'nin çatalı olarak düşünebilirsiniz.

## <a name="corert"></a>CoreRT

.NET Çekirdek çalışma zamanı.

CLR /CoreCLR'nin aksine CoreRT sanal bir makine değildir, bu da [jit](#jit)içermediği için anında kod oluşturma ve çalıştırma olanaklarını içermediği anlamına gelir. Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (RTTI) ve yansıma yeteneği içerir. Ancak, yazı sistemi yansıma için meta veri gerekli olmayacak şekilde tasarlanmıştır. Bu, gereksiz meta verileri birbirine bağlayabilen ve (daha da önemlisi) uygulamanın kullanmadığı kodu tanımlayabilen bir [AOT](#aot) takım zincirine sahip olmasını sağlar. CoreRT geliştirilmekte.

Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).

## <a name="cross-platform"></a>platformlar arası

Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde, her biri için özel olarak yeniden yazmak zorunda kalmadan kullanılabilen bir uygulama geliştirme ve yürütme olanağı. Bu, kodun yeniden kullanılmasını ve farklı platformlardaki uygulamalar arasında tutarlılık sağlar.

## <a name="ecosystem"></a>Ekosistem

Belirli bir teknoloji için uygulamalar oluşturmak ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.

".NET ekosistemi" terimi, üçüncü taraf uygulamaları ve kitaplıkları dahil etmede ".NET yığını" gibi benzer terimlerden farklıdır. Bir cümlede bir örnek aşağıda verilmiştir:

- [".NET Standardının](#net-standard) arkasındaki motivasyon .NET ekosisteminde daha fazla tekdüzelik oluşturmaktır."

## <a name="framework"></a>çerçeve

Genel olarak, belirli bir teknolojiye dayalı uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonu. Bu genel anlamda, ASP.NET Çekirdek ve Windows Formları uygulama çerçevelerine örnektir. Ayrıca [kitaplık](#library)bakın.

"Çerçeve" sözcüğünün aşağıdaki terimlerde daha spesifik bir teknik anlamı vardır:

- [.NET Çerçevesi](#net-framework)
- [hedef çerçeve](#target-framework)
- [TFM (hedef çerçeve takma adıyla)](#tfm)

Varolan belgelerde "çerçeve" bazen [.NET'in uygulanmasını](#implementation-of-net)ifade eder. Örneğin, bir makale .NET Core'u bir çerçeve olarak adlandırabilir. Bu kafa karıştırıcı kullanımı belgelerden ortadan kaldırmayı planlıyoruz.

## <a name="gc"></a>GC

Çöp toplayıcısı.

Çöp toplayıcı otomatik bellek yönetiminin bir uygulamasıdır.  GC, artık kullanılmayan nesneler tarafından işgal edilen belleği serbest eder.

[Bkz. Çöp Toplama](garbage-collection/index.md).

## <a name="il"></a>IL

Ara dil.

C# gibi üst düzey .NET dilleri, Ara Dil (IL) olarak adlandırılan donanım-agnostik yönerge kümesine kadar derlenir. IL bazen MSIL (Microsoft IL) veya CIL (Ortak IL) olarak adlandırılır.

## <a name="jit"></a>JIT

Tam zamanında derleyici.

[AOT'ye](#aot)benzer şekilde, bu derleyici [IL'yi](#il) işlemcinin anladığı makine koduna çevirir. AOT'nin aksine, JIT derlemesi isteğe bağlı olarak gerçekleşir ve kodun çalışması gereken makinede gerçekleştirilir. JIT derlemesi uygulamanın yürütülmesi sırasında oluştuğundan derleme süresi çalışma süresinin bir parçasıdır. Bu nedenle, JIT derleyicileri, kodu en iyi duruma getirmek için harcanan zamanı, ortaya çıkan kodun oluşturabileceği tasarruflara göre dengelemek zorunda kalır. Ama bir JIT gerçek donanım bilir ve farklı uygulamalar gemi sahip geliştiriciler ücretsiz olabilir.

## <a name="implementation-of-net"></a>.NET uygulaması

.NET'in bir uygulaması aşağıdakileri içerir:

- Bir veya daha fazla çalışma saatleri. Örnekler: CLR, CoreCLR, CoreRT.
- .NET Standardının bir sürümünü uygulayan ve ek API'ler içerebilen bir sınıf kitaplığı. Örnekler: .NET Framework Base Sınıf Kitaplığı, .NET Çekirdek Taban Sınıf Kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi. Örnekler: ASP.NET, Windows Formları ve WPF .NET Çerçevesi'ne dahildir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.

.NET uygulamalarına örnekler:

- [.NET Çerçevesi](#net-framework)
- [.NET Core](#net-core)
- [Evrensel Windows Platformu (UWP)](#uwp)

## <a name="library"></a>kitaplık

Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API koleksiyonu. .NET kitaplığı bir veya daha fazla [derlemeden](#assembly)oluşur.

Kitaplık ve [çerçeve](#framework) sözcükleri genellikle eş anlamlı olarak kullanılır.

## <a name="metapackage"></a>metapaketi

Kendi kitaplığı olmayan ancak yalnızca bağımlılıkların bir listesi olan Bir NuGet paketi. Dahil edilen paketler isteğe bağlı olarak bir hedef çerçeve için API'yi kurabilir.

Bkz. [Paketler, Metapaketler ve Çerçeveler](../core/packages.md)

## <a name="mono"></a>Mono

Mono, çoğunlukla küçük bir çalışma süresi gerektiğinde kullanılan açık kaynak kodlu, [çapraz platform](#cross-platform) .NET uygulamasıdır. Android, Mac, iOS, tvOS ve watchOS'taki Xamarin uygulamalarına güç veren ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanan çalışma zamanıdır.

Şu anda yayınlanan tüm .NET Standard sürümlerini destekler.

Tarihsel olarak, Mono .NET Framework'ün daha büyük API'sini uyguladı ve Unix'teki en popüler yeteneklerden bazılarını taklit etti. Bazen Unix'teki bu özelliklere dayanan .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanında derleyici ile kullanılır, ancak aynı zamanda iOS gibi platformlarda kullanılan tam bir statik derleyici (ileri-zaman derleme) özellikleri.

Mono hakkında daha fazla bilgi edinmek için [Mono belgelerine](https://www.mono-project.com/docs/)bakın.

## <a name="net"></a>.NET

[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terim. Her zaman büyük harfle, asla ".Net".

[.NET Kılavuzuna](index.md) Bakın

## <a name="net-core"></a>.NET Core

.NET'in çapraz platform, yüksek performanslı, açık kaynak uygulaması. Core Common Language Runtime (CoreCLR), Core AOT Runtime (CoreRT, geliştirme), Core Base Sınıf Kitaplığı ve Core SDK'yı içerir.

Bkz. [.NET Core](../core/index.md).

## <a name="net-core-cli"></a>.NET Core CLI

.NET Core uygulamalarını geliştirmek için bir çapraz platform araç zinciri.

Bkz. [.NET Çekirdek CLI](../core/tools/index.md).

## <a name="net-core-sdk"></a>.NET Core SDK

Geliştiricilerin .NET Core uygulamaları ve kitaplıkları oluşturmasına olanak tanıyan kitaplıklar ve araçlar kümesi. Uygulama oluşturmak için [.NET Core CLI'yi,](#net-core-cli) .NET Core kitaplıklarını ve uygulamaları oluşturmak ve çalıştırmak için çalışma süresini ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran*dotnet(dotnet.exe)* içerir.

Bkz. [.NET Core SDK Genel Bakış](../core/sdk.md).

## <a name="net-framework"></a>.NET Framework

.NET'in yalnızca Windows'da çalışan bir uygulaması. Ortak Dil Çalışma Zamanı (CLR), Temel Sınıf Kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.

Bkz. [.NET Çerçeve Rehberi](../framework/index.md).

## <a name="net-native"></a>.NET Yerel

Tam zamanında (JIT) aksine, yerel kodu zamanından önce (AOT) üreten bir derleyici araç zinciri.

Derleme, geliştiricinin makinesinde C++ derleyicisi ve bağlayıcısının çalışma şekline benzer şekilde gerçekleşir. Kullanılmayan kodu kaldırır ve en iyi duruma çıkarmak için daha fazla zaman harcar. Kitaplıklardan kod ayıklar ve bunları yürütülebilir kodlarla birleştirir. Sonuç, tüm uygulamayı temsil eden tek bir modüldür.

UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir. Artık Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.

Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)

## <a name="net-standard"></a>.NET Standard

Her .NET uygulamasında bulunan .NET API'lerinin resmi bir belirtimi.

.NET Standart belirtimi bazen belgelerde kitaplık olarak adlandırılır. Kitaplık API uygulamalarını içerdiğinden, yalnızca belirtimler (arabirimler) değil, .NET Standard'a "kitaplık" demek yanıltıcıdır. .NET Standart metapaketinin adı dışında bu kullanımı belgelerden ortadan kaldırmayı`NETStandard.Library`planlıyoruz.

Bkz. [.NET Standart](net-standard.md).

## <a name="ngen"></a>Ngen

Yerli (görüntü) nesil.

Bu teknolojiyi kalıcı bir JIT derleyicisi olarak düşünebilirsiniz. Genellikle kodun yürütüldüğü makinede kod derler, ancak derleme genellikle yükleme zamanında gerçekleşir.

## <a name="package"></a>Paket

NuGet paketi &mdash; veya yalnızca &mdash; bir paket, yazar adı gibi ek meta verilerin yanı sıra aynı adı taşıyan bir veya daha fazla derlemeye sahip bir *.zip* dosyasıdır.

*.zip* dosyası *.nupkg* uzantısına sahiptir ve birden çok hedef çerçevesi ve sürümü yle kullanılmak üzere *.dll* dosyaları ve *.xml* dosyaları gibi varlıklar içerebilir. Bir uygulamaya veya kitaplıkta yüklendiğinde, uygulama veya kitaplık tarafından belirlenen hedef çerçeveye göre uygun varlıklar seçilir. Arabirimi tanımlayan varlıklar *ref* klasöründe, uygulamayı tanımlayan varlıklar *ise lib* klasöründedir.

## <a name="platform"></a>platform

Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve çalıştırılaç donanımı.

Cümlelerdeki kullanım örnekleri şunlardır:

- ".NET Core .NET bir çapraz platform uygulamasıdır."
- "PCL profilleri Microsoft platformlarını temsil ederken,.NET Standardı platforma agnostiktir."

.NET dokümantasyonu sık sık ".NET platformu"nu tüm uygulamaları içeren .NET veya .NET yığınının uygulanması anlamına gelir. Bu kullanımların her ikisi de birincil (işletim sistemi/donanım) anlamı ile karıştırılma eğilimindedir, bu nedenle bu kullanımları belgelerden ortadan kaldırmayı planlıyoruz.

## <a name="runtime"></a>çalışma zamanı

Yönetilen bir programın yürütme ortamı.

İşletim sistemi çalışma zamanı ortamının bir parçasıdır, ancak .NET çalışma zamanının bir parçası değildir. Aşağıda .NET çalışma saatlerine ait bazı örnekler verilmiştir:

- Ortak Dil Çalışma Zamanı (CLR)
- Çekirdek Ortak Dil Çalışma Süresi (CoreCLR)
- .NET Yerel (UWP için)
- Mono çalışma süresi

.NET dokümantasyonu bazen .NET'in uygulanması anlamına gelir. Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:

- "Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular."
- "Birden çok çalışma zamanında çalışması amaçlanan kitaplıklar bu çerçeveyi hedeflemelidir." (.NET Standardına atıfta bulunarak)
- "Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular. … Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standart sürümünün reklamını yapan ..."

Bu tutarsız kullanımı ortadan kaldırmayı planlıyoruz.

## <a name="stack"></a>yığın

Uygulamaları oluşturmak ve çalıştırmak için birlikte kullanılan programlama teknolojileri kümesi.

".NET yığını" .NET Standard ve tüm .NET uygulamalarını ifade eder. ".NET yığını" deyimi .NET'in bir uygulamasına atıfta bulunabilir.

## <a name="target-framework"></a>hedef çerçeve

Bir .NET uygulamasının veya kitaplığın güvendiği API koleksiyonu.

Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesinin belirtimi olan .NET Standard'ın (örneğin, .NET Standart 2.0) bir sürümünü hedefleyebilir. Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API'lere erişebilir. Örneğin, Xamarin.iOS hedefleyen bir uygulama Xamarin sağlanan iOS API sarmalayıcılarına erişebilir.

Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API'ler, bir .NET uygulamasının bir sisteme yüklediği derlemeler tarafından tanımlanır ve bu da uygulama çerçevesi API'lerini (örneğin, ASP.NET, WinForms) içerebilir. Paket tabanlı hedef çerçeveler (.NET Standardı ve .NET Core gibi) için, çerçeve API'leri uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır. Bu durumda, hedef çerçeve örtülü olarak çerçeveyi oluşturan tüm paketlere başvuran bir meta paketi belirtir.

Bkz. [Hedef Çerçeveler](frameworks.md).

## <a name="tfm"></a>Tfm

Hedef çerçeve takma.

Bir .NET uygulamasının veya kitaplığın hedef çerçevesini belirtmek için standartlaştırılmış belirteç biçimi. Hedef çerçeveler genellikle kısa bir adla başvurulmaktadır. `net462` Uzun formlu TFM'ler (. NETFramework,Sürüm=4.6.2) vardır, ancak genellikle hedef çerçeve belirtmek için kullanılmaz.

Bkz. [Hedef Çerçeveler](frameworks.md).

## <a name="uwp"></a>UWP

Evrensel Windows Platformu.

Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows uygulamaları ve yazılımları oluşturmak için kullanılan .NET uygulaması. Cd'ler, tabletler, phablet'ler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı türde aygıtları birletmek üzere tasarlanmıştır. UWP, merkezi bir uygulama deposu, yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API'si gibi birçok hizmet sağlar. Uygulamalar C++, C#, Visual Basic ve JavaScript ile yazılabilir. C# ve Visual Basic kullanırken .NET API'leri .NET Core tarafından sağlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Kılavuzu](index.md)
- [.NET Çerçeve Rehberi](../framework/index.md)
- [.NET Core](../core/index.md)
- [ASP.NET Genel Bakış](/aspnet/index#pivot=aspnet)
- [ASP.NET Çekirdek Genel Bakış](/aspnet/index#pivot=core)
