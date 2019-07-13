---
title: .NET Portability Analyzer - .NET
description: '.NET Core, .NET standart, UWP ve Xamarin de dahil olmak üzere çeşitli .NET uygulamaları arasında nasıl taşınabilir kodunuz: değerlendirilecek .NET Portability Analyzer aracını kullanmayı öğrenin.'
ms.date: 07/10/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: f05d4f4a2fce8fa9a4d2e334f44190ea37335038
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859778"
---
# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzer

Çok platformlu destek Kitaplıklarınızı mu oluşturmak istiyorsunuz? Uygulamanız diğer .NET uygulamaları ve .NET Core, .NET standart, UWP ve Xamarin iOS, Android ve Mac için dahil olmak üzere ile uyumlu hale getirmek için ne kadar iş gereklidir görmek ister misiniz? [.NET Portability Analyzer](https://github.com/microsoft/dotnet-apiport) nasıl programınızı .NET uygulamaları arasında derlemeler analiz ederek esnektir üzerinde ayrıntılı bir rapor sağlayan bir araçtır. Taşınabilirlik Çözümleyicisi olarak sunulan bir [Visual Studio Uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), derleme proje başına ve olarak analiz eder bir [ApiPort konsol uygulaması](https://aka.ms/apiportdownload), derlemeler tarafından belirtilen dosya veya dizin analiz eder.

## <a name="common-targets"></a>Ortak hedefler

* [.NET core](../../core/index.md): Modüler bir tasarım olan, yan yana artırdığını ve platformlar arası senaryolar hedefler. Yan yana diğer uygulamaları bozmadan yeni .NET Core sürümleri benimsemenizi sağlar. Amacınız destekleyen platformlar arası .NET Core uygulamanızın bağlantı noktasına ise, bu önerilen bir hedeftir. 
* . [NET standart](../../standard/net-standard.md): Tüm .NET uygulamalarında kullanılabilir .NET standart API'ler de dahildir. Amacınız, tüm .NET üzerinde çalışan kitaplığınızı yapmak için desteklenen platformları ise, bu hedef önerilir.  
* [ASP.NET Core](/aspnet/core): Modern web-.NET Core üzerine yapılandırılan çerçevesi. Amacınız, birden çok platformu desteklemek için .NET Core web uygulamanıza bağlantı noktasına ise, bu önerilen bir hedeftir.
* .NET core + [Uzantılar](../../core/porting/windows-compat-pack.md): .NET Framework kullanılabilir teknolojilerin birçoğu sağlayan Windows Uyumluluk Paketi yanı sıra .NET Core API'ları içerir. Uygulamanızı .NET Framework Windows üzerinde .NET Core taşıma için önerilen bir hedeftir.
* .NET standard + [Uzantılar](../../core/porting/windows-compat-pack.md): .NET Framework kullanılabilir teknolojilerin birçoğu sağlayan Windows Uyumluluk Paketi yanı sıra .NET standart API'ler de dahildir. Windows üzerinde .NET Core için .NET Framework kitaplığınızda taşıma için önerilen bir hedeftir.

## <a name="how-to-use-the-net-portability-analyzer"></a>.NET Portability Analyzer'ı kullanma

Visual Studio'da .NET Portability Analyzer'ı kullanmaya başlamak için öncelikle uzantısını indirip ihtiyacınız [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Visual Studio 2017 ve sonraki sürümlerinde çalışır. Visual Studio yapılandırma **Çözümle** > **taşınabilirlik Çözümleyicisi ayarları** , hedef .NET platformları/değerlendirmek istediğiniz sürümleri olan platformları seçin Taşınabilirlik boşlukları geçerli derlemenizi oluşturulduğu platform/sürümü ile karşılaştırma.

![Taşınabilirlik ekran görüntüsü](./media/portability-analyzer/portability-screenshot.png)

ApiPort kullanabilirsiniz konsol uygulaması, indirdiği [ApiPort depo](http://aka.ms/apiportdownload). Kullanabileceğiniz `listTargets` komutu kullanılabilir hedef listesini görüntülemek ve ardından hedef platformları belirterek çekme seçeneği `-t` veya `--target` komut seçeneği. 

### <a name="analyze-portability"></a>Taşınabilirlik analiz edin
Tüm Visual Studio projenizde analiz etmek için projenize sağ **Çözüm Gezgini** seçip **analiz derleme taşınabilirlik**. Aksi takdirde, Git **Çözümle** menü ve select **analiz derleme taşınabilirlik**. Burada, projenizin yürütülebilir dosyası veya DLL'ı seçin.

![Çözüm Gezgini'nden taşınabilirlik Çözümleyicisi](./media/portability-analyzer/portability-solution-explorer.png)

Ayrıca [ApiPort konsol uygulaması](https://aka.ms/apiportdownload). 

* Geçerli dizin analiz etmek için aşağıdaki komutu yazın: `ApiPort.exe analyze -f .`
* Belirli bir .dll dosyaları listesini analiz etmek için aşağıdaki komutu yazın: `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Çalıştırma `ApiPort.exe -?` daha fazla yardım almak için

Sahibi olduğunuz ve bağlantı noktası ve uygulamanızın bağımlı, ancak sahip olmadığınız ve aktaramaz dosyaları hariç tutmak istediğiniz tüm ilgili exe ve dll dosyaları dahil önerilir. Bu size en uygun taşınabilirlik rapor sunar.  

### <a name="view-and-interpret-portability-result"></a>Görüntüleme ve taşınabilirlik sonucu yorumlama

Hedef Platform tarafından desteklenmeyen API raporda görünür. Visual Studio'da analiz çalıştırdıktan sonra uygulamanızın .NET taşınabilirlik rapor dosyası bağlantısı açılır görürsünüz. Kullandıysanız [ApiPort konsol uygulaması](https://aka.ms/apiportdownload), .NET taşınabilirlik raporunuzu belirttiğiniz biçimde dosyası olarak kaydedilir. Bir Excel dosyasında varsayılandır ( *.xlsx*) geçerli dizininizde.

#### <a name="portability-summary"></a>Taşınabilirlik özeti 

![Taşınabilirlik özeti](./media/portability-analyzer/portabilitysummary.png)

Taşınabilirlik Özet bölümünde rapor gösterir çalıştırmaya dahil her derleme için taşınabilirlik yüzdesi. .NET Framework API'ları %89.74 önceki örnekte kullanılan `ConsoleAppFramework` uygulama, .NET Core + uzantılar v2.2 içinde kullanılabilir. Birden çok bütünleştirilmiş koda karşı .NET Portability Analyzer aracını gerekiyorsa, her derleme taşınabilirlik Özeti raporunda bir satır olması gerekir.

#### <a name="details"></a>Ayrıntılar

![Taşınabilirlik ayrıntıları](./media/portability-analyzer/portabilitydetails.png)

Rapor ayrıntıları bölümü, Hedef platformlar birinden API'leri eksik listeler. 

 - Hedef türü: türü hedef Platform API'SİNDEN eksik 
 - Hedef üye: hedef platformdan yöntemi eksik 
 - Derleme adı: eksik API kendini .NET Framework derlemesi. 
 - Her bir seçili hedef platformlar ".NET Core" gibi bir sütun şöyledir: "Desteklenmiyor" değeri, API, bu hedef platformda desteklenmiyor anlamına gelir. 
 - Değişiklikleri önerilen: API veya değiştirmek için teknoloji önerilir. Şu anda, bu alan boş veya çok sayıda API'leri için güncel kalır. API'ları çok sayıda nedeniyle, bu kalmasını sağlamak için büyük zorluk sahibiz. Müşterilere yardımcı olacak bilgiler sağlamak için alternatif çözümler, arıyoruz.

#### <a name="missing-assemblies"></a>Derlemeleri eksik

![Taşınabilirlik ayrıntıları](./media/portability-analyzer/missingassemblies.png)

Raporunuzda eksik derlemeleri bölümünde bulabilirsiniz. Bu, bu derlemelerin listesini, analiz edilen derlemeler tarafından başvurulur ve çözümlenmedi bildirir. Sahip olduğunuz bir derleme ise, API düzey ayrıntılı taşınabilirlik rapor alabilmesi için API taşınabilirlik Çözümleyicisi içerir. Üçüncü taraf kitaplığı ise, bunlar hedef platformunuzu destekleyen daha yeni sürümüne sahipseniz arar. Bu durumda, en yeni sürüme taşıma göz önünde bulundurun. Sonuç olarak, bu liste, uygulamanıza bağlıdır ve hedef platformunuzu destekleyen bir sürüme sahip olduğunuzu onaylanan tüm üçüncü taraf derlemeleri içerir beklenir.  

.NET Portability Analyzer hakkında daha fazla bilgi için ziyaret [GitHub belgeleri](https://github.com/Microsoft/dotnet-apiport#documentation) ve [bir kısa bakın .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) kanal 9 videosu.


