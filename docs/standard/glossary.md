---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili koşulların anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 529b1d9142ddf7982a6712c355c10666f0414d73
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163113"
---
# <a name="net-glossary"></a>.NET Sözlüğü

Bu sözlükteki birincil hedef, .NET belgelerinde tanım olmadan sık görüntülenen seçili koşulların ve kısaltmalardan anlamaktır.

## <a name="aot"></a>AOT

Sonraki süre derleyicisi.

[JIT](#jit)'e benzer şekilde, bu derleyici Ayrıca [Il](#il) 'yi makine koduna çevirir. JıT derlemesinin aksine, uygulama yürütülmeden önce AOT derlemesi olur ve genellikle farklı bir makinede gerçekleştirilir. AOT aracı zincirleri çalışma zamanında derlenmediğinden, bu sürenin derlenmesi sırasında geçen süreyi en aza indirmeleri gerekmez. Bu, daha iyi zaman harcayabileceğiniz anlamına gelir. AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi Ayrıca çapraz modül bağlamayı ve tam program analizini gerçekleştirir, bu da tüm başvuruların izlendiği ve tek bir yürütülebilir dosyanın oluşturulduğu anlamına gelir.

Bkz. [Corert](#corert) ve [.NET Native](#net-native).

## <a name="aspnet"></a>ASP.NET

.NET Framework ile birlikte gelen özgün ASP.NET uygulamasıdır.

Bazen ASP.NET, ASP.NET Core dahil olmak üzere hem ASP.NET uygulamalarına başvuran bir şemsiye terimidir. Belirli bir örnekte yer alan dönemin, bağlam tarafından belirlendiği anlamı. Her iki uygulamayı da belirtmek için ASP.NET kullanmadığınız net bir ASP.NET 4. x öğesine başvurun.

Bkz. [ASP.net belgeleri](/aspnet/#pivot=aspnet).

## <a name="aspnet-core"></a>ASP.NET Çekirdeği

.NET Core üzerinde oluşturulan ASP.NET platformlar arası, yüksek performanslı, açık kaynaklı bir uygulama.

[ASP.NET Core belgelerine](/aspnet/#pivot=core)bakın.

## <a name="assembly"></a>derleme

*.dll* / Uygulamalar veya diğer derlemeler tarafından çağrılabilecek bir API koleksiyonu içerebilen bir. dll *. exe* dosyası.

Bir bütünleştirilmiş kod, arabirimler, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türler içerebilir. Projenin *bin* klasöründeki derlemeler bazen *ikili dosyalar*olarak adlandırılır. Ayrıca bkz. [kitaplık](#library).

## <a name="clr"></a>CLR

Ortak dil çalışma zamanı.

Tam anlamı bağlama bağlıdır, ancak ortak dil çalışma zamanı genellikle .NET Framework çalışma zamanına başvurur. CLR bellek ayırmayı ve yönetimini işler. CLR Ayrıca, yalnızca uygulamaları yürüten ancak aynı zamanda bir [JIT](#jit) derleyicisi kullanarak anında kod oluşturup derleyen bir sanal makinedir. Geçerli Microsoft CLR uygulama yalnızca Windows.

## <a name="coreclr"></a>CoreCLR

.NET Core ortak dil çalışma zamanı.

Bu CLR, CLR ile aynı kod tabanında oluşturulmuştur. Özgün olarak CoreCLR, Silverlight 'ın çalışma zamanı ve birden çok platformda çalışacak şekilde tasarlandı, özellikle Windows ve OS X. CoreCLR artık .NET Core 'un bir parçası ve CLR 'nin basitleştirilmiş bir sürümünü temsil etmektedir. Artık çok sayıda Linux dağıtımı desteği de dahil olmak üzere [platformlar arası](#cross-platform) bir çalışma zamanı. CoreCLR Ayrıca JıT ve kod yürütme özelliklerine sahip bir sanal makinedir.

## <a name="corefx"></a>CoreFx

.NET Core temel sınıf kitaplığı (BCL)

> [!TIP]
> *FX* *Framework*için temsil eder.

Sistemi oluşturan kitaplıkların bir kümesi. \* (ve sınırlı bir ölçüde Microsoft. \* ) öznitelikleri. BCL, ASP.NET Core gibi daha üst düzey uygulama çerçevelerinin üzerine inşa eden genel amaçlı, alt düzey bir çerçevedir. .NET Core BCL kaynak kodu, [.NET Core çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur. Ancak, .NET Core API 'lerinin çoğunluğu .NET Framework de mevcuttur. bu sayede CoreFX ' i .NET Framework BCL çatalını olarak düşünebilirsiniz.

## <a name="corert"></a>CoreRT

.NET Core çalışma zamanı.

CLR/CoreCLR 'nin aksine CoreRT bir sanal makine değildir, bu da bir [JIT](#jit)içermediğinden kod oluşturma ve çalıştırma tesislerini içermediği anlamına gelir. Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (rtti) ve yansıma özelliğini içerir. Ancak, tür sistemi yansıma için meta verilerin gerekli olmaması için tasarlanmıştır. Meta verilerin gerekli olmaması, gereksiz meta verileri bağlayabilen bir [AOT](#aot) araç zinciri olmasını ve (daha önemlisi) uygulamanın kullanmayan kodu belirlemenizi gerektirir. CoreRT geliştirme aşamasındadır.

[.NET Native ve CoreRT Için tanıtım](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)bölümüne bakın.

## <a name="cross-platform"></a>platformlar arası

Her biri için özel olarak yeniden yazmak zorunda kalmadan, Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde kullanılabilen bir uygulamayı geliştirebilir ve yürütebilme özelliği. Bu, farklı platformlardaki uygulamalar arasında kod yeniden kullanımını ve tutarlılığı sunar.

## <a name="ecosystem"></a>ekosistemi

Belirli bir teknoloji için uygulama derlemek ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.

".NET ekosistemi" terimi, üçüncü taraf uygulama ve kitaplıkları dahil olmak üzere ".NET Stack" gibi benzer terimlerden farklıdır. Tümcede bir örnek aşağıda verilmiştir:

- " [.NET Standard](#net-standard) arkasındaki mosyon, .net ekosisteminde daha fazla esneklik sağlamak."

## <a name="framework"></a>çerçeve

Genel olarak, belirli bir teknolojiyi temel alan uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonudur. Bu genel anlamda, ASP.NET Core ve Windows Forms uygulama çerçevelerinin örnekleridir. Ayrıca bkz. [kitaplık](#library).

"Framework" sözcüğünün aşağıdaki koşullarda daha belirli bir teknik anlamı vardır:

- [.NET Framework](#net-framework)
- [hedef çerçeve](#target-framework)
- [TFD (hedef çerçeve bilinen adı)](#tfm)

Mevcut belgelerde, "Framework" Bazen bir [.NET uygulamasını](#implementation-of-net)ifade eder. Örneğin, bir makale .NET Core Framework 'ü çağırabilir. Bu karışık kullanımı belgelerden ortadan kaldırmaya planlıyoruz.

## <a name="gc"></a>GC

Çöp toplayıcı.

Çöp toplayıcı, otomatik bellek yönetiminin bir uygulamasıdır.  GC, artık kullanılmayan nesnelerin kapladığı belleği serbest bırakır.

Bkz. [çöp toplama](garbage-collection/index.md).

## <a name="il"></a>IL

Ara dil.

C# gibi daha üst düzey .NET dilleri, ara dil (IL) olarak adlandırılan donanımdan bağımsız bir yönerge kümesine derler. Il bazen MSIL (Microsoft Il) veya CıL (ortak Il) olarak adlandırılır.

## <a name="jit"></a>JIT

Just-In-Time derleyicisi.

[AOT](#aot)'ye benzer şekilde, bu derleyici [Il](#il) 'yi işlemcinin anladığı makine koduna dönüştürür. AOT 'nin aksine JıT derleme isteğe bağlı olur ve kodun üzerinde çalışması gereken makinede gerçekleştirilir. Uygulamanın yürütülmesi sırasında JıT derlemesi gerçekleşdiğinden, derleme süresi çalışma zamanının bir parçasıdır. Bu nedenle, JıT derleyicileri, kodu en iyi duruma getirmeye harcanan süreyi, sonuçta elde edilen kodun üretebildiği tasarruflarla dengelemeye yönelik Ancak, bir JıT gerçek donanımı bilir ve geliştiricilerin farklı uygulamalar sunmalarını ücretsiz olarak kullanabilir.

## <a name="implementation-of-net"></a>.NET uygulama

.NET uygulamasının şunları içerir:

- Bir veya daha fazla çalışma zamanı. Örnekler: CLR, CoreCLR, CoreRT.
- .NET Standard bir sürümünü uygulayan ve ek API 'Ler içerebilen bir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi. Örnekler: ASP.NET, Windows Forms ve WPF .NET Framework dahil edilmiştir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.

.NET uygulamalarına örnek olarak şunlar verilebilir:

- [.NET Framework](#net-framework)
- [.NET Core](#net-core)
- [Evrensel Windows Platformu (UWP)](#uwp)

## <a name="library"></a>kitaplık

Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API 'lerin bir koleksiyonu. Bir .NET kitaplığı, bir [veya daha fazla](#assembly)derlemeden oluşur.

Sözcükler kitaplığı ve [Framework](#framework) genellikle terimler kullanılır.

## <a name="metapackage"></a>metapackage

Kendi kitaplığı olmayan ancak yalnızca bağımlılıklar listesi olan bir NuGet paketi. Dahil edilen paketler, isteğe bağlı olarak bir hedef çerçeve için API 'YI kurabilir.

## <a name="mono"></a>Mono

Mono, genellikle küçük bir çalışma zamanı gerektiğinde kullanılan açık kaynaklı, [platformlar arası](#cross-platform) bir .net uygulamasıdır. Android, Mac, iOS, tvOS ve watchOS üzerinde Xamarin uygulamalarını güçlendirir ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanılmıştır.

Şu anda yayımlanmış .NET Standard sürümlerinin tümünü destekler.

Tarihsel olarak, mono .NET Framework daha büyük API 'sini uyguladık ve UNIX üzerinde en popüler yeteneklerin bazılarını öykünüyler. Bu özellik bazen UNIX üzerinde bu özellikleri kullanan .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanında bir derleyici ile kullanılır, ancak iOS gibi platformlarda kullanılan tam bir statik derleyici (güncel derleme) da sunar.

Mono hakkında daha fazla bilgi edinmek için [mono belgelerine](https://www.mono-project.com/docs/)bakın.

## <a name="net"></a>.NET

[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terimi. Her zaman tamamen büyük harf, hiçbir zaman ".net".

Bkz. [.net Kılavuzu](index.yml)

## <a name="net-core"></a>.NET Core

.NET için platformlar arası, yüksek performanslı, açık kaynaklı bir uygulama. Çekirdek ortak dil çalışma zamanını (CoreCLR), çekirdek AOT çalışma zamanını (, geliştirme sırasında CoreRT), çekirdek temel sınıf kitaplığını ve temel SDK 'Yı içerir.

Bkz. [.NET Core](../core/index.yml).

## <a name="net-core-cli"></a>.NET Core CLI

.NET Core uygulamaları geliştirmek için platformlar arası araç zinciri.

Bkz. [.NET Core CLI](../core/tools/index.md).

## <a name="net-core-sdk"></a>.NET Core SDK

Geliştiricilerin .NET Core Uygulamaları ve kitaplıkları oluşturmalarına izin veren bir kitaplık ve araç kümesi. Uygulamalar oluşturmaya yönelik [.NET Core CLI](#net-core-cli) , uygulamalar oluşturmak ve çalıştırmak Için .NET Core kitaplıklarını ve çalışma ZAMANıNı ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran DotNet çalıştırılabilir (*dotnet.exe*) bilgilerini içerir.

[.NET Core SDK genel bakış](../core/sdk.md)bölümüne bakın.

## <a name="net-framework"></a>.NET Framework

Yalnızca Windows üzerinde çalışan bir .NET uygulamasıdır. Ortak dil çalışma zamanını (CLR), temel sınıf kitaplığını ve ASP.NET, Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.

[.NET Framework Kılavuzu](../framework/index.yml)' na bakın.

## <a name="net-native"></a>.NET Yerel

Anında yerel kod üreten bir derleyici aracı zinciri (AOT)-ın-Time (JıT) yerine.

Derleme, geliştirici makinesinde C++ derleyicisinin ve bağlayıcının çalışmasına benzer şekilde gerçekleşir. Kullanılmayan kodu kaldırır ve iyileştirerek daha fazla zaman harcamalar. Kodu kitaplıklardan ayıklar ve çalıştırılabilirle birleştirir. Sonuç, uygulamanın tamamını temsil eden tek bir modüldür.

UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir. Şimdi Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.

[.NET Native ve CoreRT tanıtımı](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) konusuna bakın

## <a name="net-standard"></a>.NET Standard

.NET API 'lerinin her bir .NET uygulamasında kullanılabilen resmi bir belirtimi.

.NET Standard belirtimine bazen belgelerde bir kitaplık denir. Bir kitaplık yalnızca belirtim (arabirimler) değil API uygulamalarını içerdiğinden, bir "Library" .NET Standard çağırmak yanıltıcıdır. .NET Standard metapackage () adı ile ilgili olarak, belgelerden bu kullanımı ortadan kaldırmaya planlıyoruz `NETStandard.Library` .

Bkz. [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Yerel (görüntü) oluşturma.

Bu teknolojiyi kalıcı bir JıT derleyicisi olarak düşünebilirsiniz. Genellikle kodun yürütüldüğü makinede kodu derler, ancak derleme genellikle yüklemesi sırasında gerçekleşir.

## <a name="package"></a>leyebilir

Bir NuGet paketi &mdash; veya yalnızca bir paket &mdash; , aynı ada sahip bir veya daha fazla bütünleştirilmiş kod içeren bir *. zip* dosyasıdır ve yazar adı gibi ek meta verilerle birlikte.

*. Zip* dosyası *. nupkg* uzantısına sahiptir ve birden çok hedef çerçeve ve sürümde kullanılmak üzere *. dll* dosyaları ve *. xml* dosyaları gibi varlıkları içerebilir. Bir uygulama veya kitaplığa yüklendiğinde, uygun varlıklar uygulama veya kitaplık tarafından belirtilen hedef çerçeveye göre seçilir. Arabirimi tanımlayan varlıklar *ref* klasöründedir ve uygulamayı tanımlayan varlıklar *lib* klasöründedir.

## <a name="platform"></a>platform

Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve üzerinde çalıştığı donanım.

Cümlelerde kullanım örnekleri aşağıda verilmiştir:

- ".NET Core, .NET 'in platformlar arası bir uygulamasıdır."
- "PCL profilleri Microsoft platformlarını temsil ederken .NET Standard platforma göre belirsizdir."

.NET belgeleri, .NET veya .NET Stack 'in tüm uygulamalar dahil bir uygulamasını ifade etmek için sık sık ".NET platformu" kullanır. Bu kullanımların her ikisi de birincil (OS/donanım) anlamı ile karıştırılmamalıdır. bu nedenle, bu kullanımları belgelerden ortadan kaldırmaya planlanıyoruz.

## <a name="runtime"></a>çalışma zamanı

Yönetilen programın yürütme ortamı.

İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir. .NET çalışma zamanlarının bazı örnekleri aşağıda verilmiştir:

- Ortak Dil Çalışma Zamanı (CLR)
- Çekirdek ortak dil çalışma zamanı (CoreCLR)
- .NET Native (UWP için)
- Mono çalışma zamanı

.NET belgeleri bazen .NET uygulamasının bir uygulamasını ifade etmek için "Runtime" kullanır. Örneğin, aşağıdaki cümleler "Runtime" ın "uygulama" ile değiştirilmelidir:

- "Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular."
- "Birden çok çalışma zamanında çalıştırılması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir." (.NET Standard başvurma)
- "Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular. … Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standard sürümünü tanıtır... "

Bu tutarsız kullanımı ortadan kaldırmaya planlıyoruz.

## <a name="stack"></a>yığın

Uygulamaları derlemek ve çalıştırmak için birlikte kullanılan bir programlama teknolojileri kümesi.

".NET Stack" .NET Standard ve tüm .NET uygulamalarını ifade eder. "A .NET Stack" ifadesi bir .NET uygulamasına başvurabilir.

## <a name="target-framework"></a>hedef çerçeve

Bir .NET uygulamasının veya kitaplığının dayandığı API 'lerin koleksiyonu.

Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesine yönelik belirtim olan .NET Standard bir sürümünü (örneğin, .NET Standard 2,0) hedefleyebilir. Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API 'lere erişim sağlar. Örneğin, Xamarin. iOS 'u hedefleyen bir uygulama Xamarin tarafından sağlanmış iOS API sarmalayıcılarını erişim altına alır.

Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API 'ler, .NET uygulamasının uygulama çerçevesi API 'Leri içerebilen bir sisteme yüklediği derlemeler tarafından tanımlanır (örneğin, ASP.NET, WinForms). Paket tabanlı hedef çerçeveler için (.NET Standard ve .NET Core gibi), çerçeve API 'Leri, uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır. Bu durumda, hedef çerçeve örtülü olarak Framework 'ü oluşturan tüm paketlere başvuran bir metapackage belirler.

Bkz. [hedef çerçeveler](frameworks.md).

## <a name="tfm"></a>TFM

Hedef Framework bilinen adı.

.NET uygulaması veya kitaplığının hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimi. Hedef çerçevelere genellikle gibi kısa bir ad başvurulur `net462` . Uzun biçimli TFMs (gibi. NETFramework, Version = 4.6.2) var, ancak genellikle bir hedef çerçeve belirtmek için kullanılmaz.

Bkz. [hedef çerçeveler](frameworks.md).

## <a name="uwp"></a>UWP

Evrensel Windows Platformu.

Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows Uygulamaları ve yazılım oluşturmak için kullanılan bir .NET uygulaması. Bilgisayar, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı cihaz türlerini içerecek şekilde tasarlanmıştır. UWP, merkezi bir App Store, bir yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API 'si gibi birçok hizmeti sağlar. Uygulamalar C++, C#, Visual Basic ve JavaScript 'te yazılabilir. C# ve Visual Basic kullanılırken .NET API 'Leri .NET Core tarafından sağlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kılavuzu](index.yml)
- [.NET Framework Kılavuzu](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [ASP.NET genel bakış](/aspnet/index#pivot=aspnet)
- [ASP.NET Core genel bakış](/aspnet/index#pivot=core)
