---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili koşulların anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 59e338de99510759e3e7acfd782915ed6dc5d988
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957579"
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

## <a name="aspnet-core"></a>ASP.NET Core

ASP.NET 'in platformlar arası, yüksek performanslı, açık kaynaklı bir uygulamasıdır.

[ASP.NET Core belgelerine](/aspnet/#pivot=core)bakın.

## <a name="assembly"></a>derleme

*.dll* / Uygulamalar veya diğer derlemeler tarafından çağrılabilecek bir API koleksiyonu içerebilen bir. dll *. exe* dosyası.

Bir bütünleştirilmiş kod, arabirimler, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türler içerebilir. Projenin *bin* klasöründeki derlemeler bazen *ikili dosyalar*olarak adlandırılır. Ayrıca bkz. [kitaplık](#library).

## <a name="bcl"></a>BCL

Temel sınıf kitaplığı. *Çerçeve kitaplıkları*olarak da bilinir.

Sistemi oluşturan kitaplıkların bir kümesi. \* (ve sınırlı bir ölçüde Microsoft. \* ) öznitelikleri. BCL, ASP.NET Core gibi daha üst düzey uygulama çerçevelerinin üzerine inşa eden genel amaçlı, alt düzey bir çerçevedir.

[.NET 5 (ve .NET Core) ve sonraki SÜRÜMLERIN](#net-5-and-later-versions) BCL kaynak kodu, [.NET çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur. .NET 'in bu yeni uygulamasına yönelik BCL API 'Lerinin çoğu .NET Framework de mevcuttur. bu sayede, bu kaynak kodu .NET Framework BCL kaynak kodunun bir çatalı olarak düşünebilirsiniz.

## <a name="clr"></a>CLR

Ortak dil çalışma zamanı.

Tam anlamı bağlama göre değişir. Ortak dil çalışma zamanı genellikle [.NET Framework](#net-framework) çalışma zamanına veya [.NET 5 (ve .NET Core) ve sonraki sürümlere](#net-5-and-later-versions)yönelik çalışma zamanına başvurur.

CLR bellek ayırmayı ve yönetimini işler. CLR Ayrıca, yalnızca uygulamaları yürüten ancak aynı zamanda bir [JIT](#jit) derleyicisi kullanarak anında kod oluşturup derleyen bir sanal makinedir.

.NET Framework için CLR uygulama yalnızca Windows ' a yöneliktir.

.NET 5 ve sonraki sürümler için CLR uygulama (çekirdek CLR olarak da bilinir) .NET Framework CLR ile aynı kod tabanından oluşturulmuştur. Başlangıçta, çekirdek CLR Silverlight 'ın çalışma zamanı ve özellikle Windows ve OS X gibi birden çok platformda çalışmak üzere tasarlanmıştır. Artık çok sayıda Linux dağıtımı desteği de dahil olmak üzere [platformlar arası](#cross-platform) bir çalışma zamanı.

Ayrıca bkz. [çalışma zamanı](#runtime).

## <a name="core-clr"></a>Çekirdek CLR

[.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)Için ortak dil çalışma zamanı.

Bkz. [clr](#clr)

## <a name="corert"></a>CoreRT

[Clr](#clr)'nin aksine corert sanal bir makine değildir, bu da bir [JIT](#jit)içermediğinden kod oluşturma ve çalıştırma tesislerini içermez. Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (rtti) ve yansıma özelliğini içerir. Ancak, tür sistemi yansıma için meta verilerin gerekli olmaması için tasarlanmıştır. Meta verilerin gerekli olmaması, gereksiz meta verileri bağlayabilen bir [AOT](#aot) araç zinciri olmasını ve (daha önemlisi) uygulamanın kullanmayan kodu belirlemenizi gerektirir. CoreRT geliştirme aşamasındadır.

[.NET Native ve CoreRT Için tanıtım](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)bölümüne bakın.

## <a name="cross-platform"></a>platformlar arası

Her biri için özel olarak yeniden yazmak zorunda kalmadan, Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde kullanılabilen bir uygulamayı geliştirebilir ve yürütebilme özelliği. Bu, farklı platformlardaki uygulamalar arasında kod yeniden kullanımını ve tutarlılığı sunar.

## <a name="ecosystem"></a>ekosistemi

Belirli bir teknoloji için uygulama derlemek ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.

".NET ekosistemi" terimi, üçüncü taraf uygulama ve kitaplıkları dahil olmak üzere ".NET Stack" gibi benzer terimlerden farklıdır. Tümcede bir örnek aşağıda verilmiştir:

- " [.NET Standard](#net-standard) arkasındaki mosyon, .net ekosisteminde daha fazla esneklik sağlamak."

## <a name="framework"></a>çerçeve

Genel olarak, belirli bir teknolojiyi temel alan uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonudur. Bu genel anlamda, ASP.NET Core ve Windows Forms uygulama çerçevelerinin örnekleridir. Ayrıca bkz. [kitaplık](#library).

"Framework" sözcüğünün aşağıdaki koşullarda farklı anlamları vardır:

- [.NET Framework](#net-framework)
- [hedef çerçeve](#target-framework)
- [TFD (hedef çerçeve bilinen adı)](#tfm)
- [çerçeveye bağımlı uygulama](../core/deploying/index.md#publish-framework-dependent)

Eski .NET belgelerinde, "Framework" Bazen bir [.NET uygulamasını](#implementation-of-net)ifade eder. Örneğin, bir makale bir Framework .NET 5 ' i çağırabilir.

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

- Bir veya daha fazla çalışma zamanı. Örnekler: [clr](#clr), [corert](#corert).
- .NET Standard bir sürümünü uygulayan ve ek API 'Ler içerebilen bir sınıf kitaplığı. Örnekler: [.NET Framework](#net-framework) ve [.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)için [BCls](#bcl) .
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi. Örnekler: [ASP.net](#aspnet), WINDOWS Forms ve WPF, .NET Framework ve .NET 5 ' de yer almaktadır.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.

.NET uygulamalarına örnek olarak şunlar verilebilir:

- [.NET Framework](#net-framework)
- [.NET 5 ve sonraki sürümleri (.NET Core 2.1-3.1 dahil)](#net-5-and-later-versions)
- [Evrensel Windows Platformu (UWP)](#uwp)
- [Mono](#mono)

## <a name="library"></a>kitaplık

Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API 'lerin bir koleksiyonu. Bir .NET kitaplığı, bir [veya daha fazla](#assembly)derlemeden oluşur.

Sözcükler kitaplığı ve [Framework](#framework) genellikle terimler kullanılır.

## <a name="mono"></a>Mono

Mono, genellikle küçük bir çalışma zamanı gerektiğinde kullanılan açık kaynaklı, [platformlar arası](#cross-platform) bir .net uygulamasıdır. Android, Mac, iOS, tvOS ve watchOS üzerinde Xamarin uygulamalarını güçlendirir ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanılmıştır.

Şu anda yayımlanmış .NET Standard sürümlerinin tümünü destekler.

Tarihsel olarak, mono .NET Framework daha büyük API 'sini uyguladık ve UNIX üzerinde en popüler yeteneklerin bazılarını öykünüyler. Bu özellik bazen UNIX üzerinde bu özellikleri kullanan .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam [zamanında bir derleyici](#jit)ile kullanılır, ancak iOS gibi platformlarda kullanılan tam bir [statik derleyici (güncel derleme)](#aot) da sunar.

[Mono belgelerine](https://www.mono-project.com/docs/)bakın.

## <a name="net"></a>.NET

[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terimi. Her zaman tamamen büyük harf, hiçbir zaman ".net".

[.NET 5](#net-5-and-later-versions) (Şu anda önizleme aşamasında) yayınlanmışsa, tüm yeni .NET geliştirme işlemleri için önerilen .NET uygulamaları olacaktır ve bu nedenle ".net" bazı bağlamlarda ".NET 5 ve sonraki sürümler" anlamına gelir.

Bkz. [.net Kılavuzu](index.yml)

## <a name="net-5-and-later-versions"></a>.NET 5 ve sonraki sürümler

.NET için platformlar arası, yüksek performanslı, açık kaynaklı bir uygulama. Ortak dil çalışma zamanı ([clr](#clr)), bir [AOT](#aot) çalışma[zamanı (,](#corert)geliştirme aşamasında), bir temel sınıf KITAPLıĞı ([BCL](#bcl)) ve [.NET SDK](#net-sdk)içerir.

Bu .NET uygulamasının önceki sürümleri .NET Core olarak bilinir. .NET 5,0, .NET Core 3,1 ' ü izleyen bir sonraki sürümdür. Sürüm 4, daha yeni bir .NET uygulamasının [.NET Framework](#net-framework)olarak bilinen eski uygulamayla karışmasını önlemek için atlandı. .NET Framework geçerli sürümü 4,8 ' dir.

Bkz. [.net](../core/index.yml).

## <a name="net-cli"></a>.NET CLı

[.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)için uygulama ve kitaplıklar geliştirmeye yönelik platformlar arası araç zinciri. .NET Core CLI olarak da bilinir.

Bkz. [.net CLI](../core/tools/index.md).

## <a name="net-core"></a>.NET Core

Bkz. [.NET 5 ve sonraki sürümler](#net-5-and-later-versions).

## <a name="net-framework"></a>.NET Framework

Yalnızca Windows üzerinde çalışan bir .NET uygulamasıdır. Ortak dil çalışma zamanını ([clr](#clr)), temel sınıf kitaplığını ([BCL](#bcl)) ve [ASP.net](#aspnet), Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.

[.NET Framework Kılavuzu](../framework/index.yml)' na bakın.

## <a name="net-native"></a>.NET Yerel

Anında yerel kod üreten bir derleyici aracı zinciri ([AOT](#aot))-ın-Time ([JIT](#jit)) yerine.

Derleme, geliştirici makinesinde C++ derleyicisinin ve bağlayıcının çalışmasına benzer şekilde gerçekleşir. Kullanılmayan kodu kaldırır ve iyileştirerek daha fazla zaman harcamalar. Kodu kitaplıklardan ayıklar ve çalıştırılabilirle birleştirir. Sonuç, uygulamanın tamamını temsil eden tek bir modüldür.

UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir. Şimdi Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.

[.NET Native ve CoreRT tanıtımı](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) konusuna bakın

## <a name="net-sdk"></a>.NET SDK

Geliştiricilerin [.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)için .NET uygulamaları ve kitaplıkları oluşturmalarına izin veren bir kitaplıklar ve araçlar kümesi. .NET Core SDK olarak da bilinir.

Uygulamalar oluşturmaya yönelik [.net CLI](#net-cli) , uygulamalar oluşturmak ve çalıştırmak için .NET, .NET kitaplıkları ve çalışma zamanı ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran DotNet çalıştırılabilir (*dotnet.exe*) içerir.

Bkz. [.NET SDK 'Ya genel bakış](../core/sdk.md).

## <a name="net-standard"></a>.NET Standard

.NET API 'lerinin her bir .NET uygulamasında kullanılabilen resmi bir belirtimi.

.NET Standard belirtimine bazen belgelerde bir kitaplık denir. Bir kitaplık yalnızca belirtim (arabirimler) değil API uygulamalarını içerdiğinden, bir "Library" .NET Standard çağırmak yanıltıcıdır.

Bkz. [.NET Standard](net-standard.md).

## <a name="ngen"></a>NGEN

Yerel (görüntü) oluşturma.

Bu teknolojiyi kalıcı bir [JIT](#jit) derleyicisi olarak düşünebilirsiniz. Genellikle kodun yürütüldüğü makinede kodu derler, ancak derleme genellikle yüklemesi sırasında gerçekleşir.

## <a name="package"></a>leyebilir

Bir NuGet paketi &mdash; veya yalnızca bir paket &mdash; , aynı ada sahip bir veya daha fazla bütünleştirilmiş kod içeren bir *. zip* dosyasıdır ve yazar adı gibi ek meta verilerle birlikte.

*. Zip* dosyası *. nupkg* uzantısına sahiptir ve birden çok hedef çerçeve ve sürümde kullanılmak üzere *. dll* dosyaları ve *. xml* dosyaları gibi varlıkları içerebilir. Bir uygulama veya kitaplığa yüklendiğinde, uygun varlıklar uygulama veya kitaplık tarafından belirtilen hedef çerçeveye göre seçilir. Arabirimi tanımlayan varlıklar *ref* klasöründedir ve uygulamayı tanımlayan varlıklar *lib* klasöründedir.

## <a name="platform"></a>platform

Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve üzerinde çalıştığı donanım.

Cümlelerde kullanım örnekleri aşağıda verilmiştir:

- ".NET Core, .NET 'in platformlar arası bir uygulamasıdır."
- "PCL profilleri Microsoft platformlarını temsil ederken .NET Standard platforma göre belirsizdir."

Eski .NET belgeleri bazen .NET veya .NET [Stack](#stack) 'in tüm uygulamalar dahil bir [uygulamasını](#implementation-of-net) ifade etmek için ".NET platformu" kullanır. Bu kullanımların her ikisi de birincil (OS/donanım) anlamını aşmaya eğilimlidir, bu nedenle bu kullanımlardan kaçınmaya çalışırız.

"Platform" ifadesi, uygulama oluşturmak ve çalıştırmak için araçlar ve kitaplıklar sağlayan yazılıma işaret eden "geliştirici platformu" cümlecide farklı anlamdadır. .NET, birçok farklı uygulama türü oluşturmak için platformlar arası, açık kaynaklı bir geliştirici platformudur.

## <a name="runtime"></a>çalışma zamanı

Genel olarak, yönetilen programın yürütme ortamı. İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir. İşte bu sözcüğün bu anlamda bazı .NET çalışma zamanları örnekleri verilmiştir:

- Ortak dil çalışma zamanı ([clr](#clr))
- .NET Native (UWP için)
- Mono çalışma zamanı

"Runtime" sözcüğünün aşağıdaki bağlamlarda farklı bir anlamı vardır:

* [.Net indirme sayfası](https://dotnet.microsoft.com/download).

  Burada "Runtime" burada [clr](#clr) 'nin bir makineye indirip yükleyebilecekleri [BCL](#bcl) (çerçeve kitaplıkları) ile birlikte, makineye [bağlı](../core/deploying/index.md#publish-framework-dependent) uygulamaları makinede çalıştırabilmeniz için bir makineye indirebilir ve yükleyebilirsiniz.

* [.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)Için [çalışma zamanı tanımlayıcısı (RID)](../core/rid-catalog.md) .

  Burada "Runtime", .NET uygulamasının üzerinde çalıştığı işletim sistemi platformu ve CPU mimarisi anlamına gelir, örneğin: `linux-x64` .

Eski .NET belgeleri bazen, aşağıdaki örneklerde olduğu gibi, [.NET uygulamasının bir uygulama](#implementation-of-net)açısından "Runtime" kullanır:

- "Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular."
- "Birden çok çalışma zamanında çalıştırılması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir." (.NET Standard başvurma)
- "Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular. … Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standard sürümünü tanıtır... "

## <a name="stack"></a>yığın

Uygulamaları derlemek ve çalıştırmak için birlikte kullanılan bir programlama teknolojileri kümesi.

".NET Stack" .NET Standard ve tüm .NET uygulamalarını ifade eder. "A .NET Stack" ifadesi bir .NET uygulamasına başvurabilir.

## <a name="target-framework"></a>hedef çerçeve

Bir .NET uygulamasının veya kitaplığının dayandığı API 'lerin koleksiyonu.

Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesine yönelik belirtim olan .NET Standard bir sürümünü (örneğin, .NET Standard 2,0) hedefleyebilir. Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API 'lere erişim sağlar. Örneğin, Xamarin. iOS 'u hedefleyen bir uygulama Xamarin tarafından sağlanmış iOS API sarmalayıcılarını erişim altına alır.

Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API 'ler, .NET uygulamasının uygulama çerçevesi API 'Leri içerebilen bir sisteme yüklediği derlemeler tarafından tanımlanır (örneğin, ASP.NET, WinForms). Paket tabanlı hedef çerçeveler için (.NET Standard ve .NET Core gibi), çerçeve API 'Leri, uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır. Bu durumda, hedef çerçeve dolaylı olarak çerçeveyi oluşturan tüm paketlere başvuran bir paketi belirtir.

Bkz. [hedef çerçeveler](frameworks.md).

## <a name="tfm"></a>TFM

Hedef Framework bilinen adı.

.NET uygulaması veya kitaplığının hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimi. Hedef çerçevelere genellikle gibi kısa bir ad başvurulur `net462` . Uzun biçimli TFMs (gibi. NETFramework, Version = 4.6.2) var, ancak genellikle bir hedef çerçeve belirtmek için kullanılmaz.

Bkz. [hedef çerçeveler](frameworks.md).

## <a name="uwp"></a>UWP

Evrensel Windows Platformu.

Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows Uygulamaları ve yazılım oluşturmak için kullanılan bir .NET uygulaması. Bilgisayar, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı cihaz türlerini içerecek şekilde tasarlanmıştır. UWP, merkezi bir App Store, bir yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API 'si gibi birçok hizmeti sağlar. Uygulamalar C++, C#, Visual Basic ve JavaScript 'te yazılabilir. C# ve Visual Basic kullanılırken .NET API 'Leri .NET 5 (ve .NET Core) ve sonraki sürümler tarafından sağlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kılavuzu](index.yml)
- [.NET Framework Kılavuzu](../framework/index.yml)
- [.NET Core](../core/index.yml)
- [ASP.NET genel bakış](/aspnet/index#pivot=aspnet)
- [ASP.NET Core genel bakış](/aspnet/index#pivot=core)
