---
title: .NET taşınabilirlik Çözümleyicisi-.NET
description: .Net taşınabilirlik Çözümleyicisi aracını kullanarak kodunuzun, .NET Core, .NET Standard, UWP ve Xamarin gibi çeşitli .NET uygulamaları arasında nasıl olduğunu değerlendirmek için nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 7fe5aafe1ad8bf87883ebe27f2aa4fb102a01e45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501812"
---
# <a name="the-net-portability-analyzer"></a>.NET taşınabilirlik Çözümleyicisi

Kitaplıklarınızın çok platformlu desteklemesini sağlamak istiyor musunuz? .NET Framework uygulamanızın .NET Core üzerinde çalışmasını sağlamak için ne kadar iş gerektiğini görmek mi istiyorsunuz? [.Net taşınabilirlik Çözümleyicisi](https://github.com/microsoft/dotnet-apiport) , derlemeleri çözümleyen ve belirtilen hedeflenen .net platformlarınızda taşınabilir uygulamalar veya kitaplıklar için eksik olan .NET API 'lerinde ayrıntılı bir rapor sağlayan bir araçtır. Taşınabilirlik Çözümleyicisi, her proje için bir derlemeyi çözümleyen ve belirtilen dosya veya dizin tarafından derlemeleri çözümleyen bir [Apiport konsol uygulaması](https://aka.ms/apiportdownload)olarak bir [Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)olarak sunulur.

Projenizi, .NET Core gibi yeni platformu hedefleyecek şekilde dönüştürdükten sonra, özel durumları ve diğer uyumluluk sorunlarını oluşturan API 'Leri belirlemek için Roslyn tabanlı [API Çözümleyicisi aracını](api-analyzer.md) kullanabilirsiniz <xref:System.PlatformNotSupportedException> .

## <a name="common-targets"></a>Ortak hedefler

- [.NET Core](../../core/index.yml): modüler bir tasarıma sahiptir, yan yana yüklemeyi destekler ve platformlar arası senaryoları hedefler. Yan yana yükleme, diğer uygulamaları bozmadan yeni .NET Core sürümlerini benimsemenizi sağlar. Amacınız uygulamanızın .NET Core 'a bağlantı noktası olması ve birden çok platformu desteklemesi gerekiyorsa, bu önerilen hedeftir.
- . [NET Standard](../net-standard.md): tüm .NET uygulamalarında bulunan .NET Standard API 'leri içerir. Amacınız, kitaplığınızı .NET tarafından desteklenen tüm platformlarda çalıştırmak ise, bu önerilen hedeftir.
- [ASP.NET Core](/aspnet/core): .NET Core üzerinde oluşturulmuş modern bir Web çerçevesi. Amacınız, Web uygulamanızın birden çok platformu desteklemek üzere .NET Core 'a bağlantı noktası olması durumunda önerilen hedeftir.
- .NET Core + [Platform uzantıları](../../core/porting/windows-compat-pack.md): .NET Core API 'lerinin yanı sıra, .NET Framework kullanılabilir teknolojilerin çoğunu sağlayan Windows Uyumluluk Paketi ' ne ek olarak dahildir. Bu, uygulamanızın Windows 'da .NET Framework .NET Core 'a taşıma için önerilen bir hedeftir.
- .NET Standard + [Platform uzantıları](../../core/porting/windows-compat-pack.md): .NET Framework kullanılabilir teknolojilerin çoğunu sağlayan Windows Uyumluluk Paketi 'ne ek olarak .NET Standard API 'leri içerir. Bu, kitaplığınızın .NET Framework Windows üzerinde .NET Core 'a taşıma için önerilen bir hedeftir.

## <a name="how-to-use-the-net-portability-analyzer"></a>.NET taşınabilirlik Çözümleyicisi 'ni kullanma

Visual Studio 'da .NET taşınabilirlik Çözümleyicisi 'ni kullanmaya başlamak için önce uzantıyı [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)indirip yüklemeniz gerekir. Visual Studio 2017 ve sonraki sürümlerinde çalışmaktadır. Visual Studio 'da **Analyze**  >  **taşınabilirlik Çözümleyicisi ayarlarını** analiz ederek yapılandırın ve geçerli derlemelerinizin oluşturulduğu platform/sürümle kıyaslanması gereken taşınabilirlik boşluklarını değerlendirmek istediğiniz .net platformları/sürümleri olan hedef Platformlarınızı seçin.

![Taşınabilirlik Çözümleyicisi 'nin ekran görüntüsü.](./media/portability-analyzer/portability-screenshot.png)

Ayrıca, ApiPort konsol uygulamasını da kullanabilir, [apiport deposundan](https://aka.ms/apiportdownload)indirebilirsiniz. `listTargets`Kullanılabilir hedef listesini göstermek için komut seçeneğini kullanabilirsiniz, ardından `-t` veya komut seçeneğini belirterek hedef platformları seçebilirsiniz `--target` .

> [!IMPORTANT]
> Aracı çalıştırırken sonuç yoksa, varsayılan hedefler kullanılamayabilir. Bu sorunla karşılaşırsanız, lütfen açık hedefleri eklemediğinizden emin olun.

### <a name="solution-wide-view"></a>Çözüm genelinde görünüm

Birçok projeyle bir çözümü çözümlemede yararlı bir adım, derlemelerin hangi alt kümesinin ne olduğunu anlamak için bağımlılıkları görselleştirmektir. Genel öneri, bir bağımlılık grafiğindeki yaprak düğümleri ile başlayan bir alt yaklaşımda analizin sonuçlarının uygulanması için kullanılır.

Bunu almak için aşağıdaki komutu çalıştırabilirsiniz:

```
ApiPort.exe analyze -r DGML -f [directory or file]
```

Bunun sonucu, Visual Studio 'da açıldığında aşağıdaki gibi görünür:

![DGML analizinin ekran görüntüsü.](./media/portability-analyzer/dgml-example.png)

### <a name="analyze-portability"></a>Taşınabilirliği çözümle
Visual Studio 'daki tüm projenizi çözümlemek için **Çözüm Gezgini** ' de projenize sağ tıklayın ve **derleme taşınabilirliği çözümle**' yi seçin. Aksi takdirde, **Çözümle** menüsüne gidin ve **derleme taşınabilirliği çözümle**' yi seçin. Buradan projenizin yürütülebilir dosyasını veya DLL 'sini seçin.

![Çözüm Gezgini 'ten taşınabilirlik Çözümleyicisi ekran görüntüsü.](./media/portability-analyzer/portability-solution-explorer.png)

[Apiport konsol uygulamasını](https://aka.ms/apiportdownload)da kullanabilirsiniz.

- Geçerli dizini çözümlemek için aşağıdaki komutu yazın:`ApiPort.exe analyze -f .`
- Belirli bir. dll dosyaları listesini analiz etmek için aşağıdaki komutu yazın:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- `ApiPort.exe -?`Daha fazla yardım almak için çalıştırın

Sahip olduğunuz ve bağlantı noktası yapmak istediğiniz tüm ilgili exe ve DLL dosyalarını dahil etmeniz ve uygulamanızın bağlı olduğu dosyaları dışlayamazsınız, ancak bağlantı noktası kullanamazsınız. Bu, size en uygun taşınabilirlik raporu sağlar.

### <a name="view-and-interpret-portability-result"></a>Taşınabilirlik sonucunu görüntüleme ve yorumlama

Raporda yalnızca bir hedef platform tarafından desteklenmeyen API 'Ler görüntülenir.
Analysis 'i Visual Studio 'da çalıştırdıktan sonra, .NET taşınabilirlik rapor dosyası bağlantısı açılır bilgilerinizi görürsünüz. [Apiport konsol uygulamasını](https://aka.ms/apiportdownload)kullandıysanız, .net taşınabilirlik raporunuz belirttiğiniz biçimde bir dosya olarak kaydedilir. Varsayılan değer, geçerli dizininizdeki bir Excel dosyasında (*. xlsx*) bulunur.

#### <a name="portability-summary"></a>Taşınabilirlik Özeti

![Taşınabilirlik özetinin ekran görüntüsü.](./media/portability-analyzer/api-catalog-portablility-summary.png)

Raporun taşınabilirlik Özeti bölümünde, çalıştırmada bulunan her derleme için taşınabilirlik yüzdesi gösterilmektedir. Önceki örnekte, uygulamada kullanılan .NET Framework API 'Lerinin% 71,24 ' u `svcutil` .NET Core + platform uzantılarında sunulmaktadır. .NET taşınabilirlik Çözümleyicisi aracını birden çok derlemeye karşı çalıştırırsanız, her derlemenin taşınabilirlik Özeti raporunda bir satırı olması gerekir.

#### <a name="details"></a>Ayrıntılar

![Taşınabilirlik ayrıntılarının ekran görüntüsü.](./media/portability-analyzer/api-catalog-portablility-details.png)

Raporun **Ayrıntılar** bölümünde, seçilen **hedeflenen platformların**hiçbirinde eksik olan API 'ler listelenir.

- Hedef türü: tür, hedef platformdan eksik API 'ye sahip
- Hedef üye: Yöntem bir hedef platformda yok
- Bütünleştirilmiş kod adı: eksik API 'nin üzerinde bulunduğu .NET Framework derlemesi.
- Seçilen hedef platformların her biri, ".NET Core": "desteklenmeyen" değeri gibi bir sütundur ve bu hedef platformda API 'nin desteklenmediği anlamına gelir.
- Önerilen değişiklikler: olarak değiştirilecek önerilen API veya teknoloji. Şu anda, birçok API için bu alan boş veya güncel değil. Çok sayıda API nedeniyle, güncel tutmanın önemli bir zorluğu vardır. Müşterilere yararlı bilgiler sağlamak için alternatif çözümlere bakıyoruz.

#### <a name="missing-assemblies"></a>Eksik derlemeler

![Eksik derlemelerin ekran görüntüsü.](./media/portability-analyzer/api-catalog-missing-assemblies.png)

Raporunuzda eksik derlemeler bölümünü bulabilirsiniz. Bu bölüm, çözümlenmiş derlemeleriniz tarafından başvurulan ve çözümlenmemiş derlemelerin bir listesini içerir. Sahip olduğunuz bir derlemedir, bunun için ayrıntılı, API düzeyi taşınabilirlik raporu alabilmeniz için API taşınabilirlik Çözümleyicisi ' ni çalıştırın. Üçüncü taraf bir kitaplıksa, hedef platformunuzu destekleyen daha yeni bir sürüm olup olmadığını denetleyin ve daha yeni sürüme geçmeyi düşünün. Sonuç olarak, listenin, hedef platformunuzu destekleyen bir sürümü olan, uygulamanızın bağımlı olduğu tüm üçüncü taraf derlemelerini içermesi gerekir.

.NET taşınabilirlik Çözümleyicisi hakkında daha fazla bilgi için [GitHub belgelerini](https://github.com/Microsoft/dotnet-apiport#documentation) ziyaret edin ve [.net taşınabilirlik Çözümleyicisi](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Kanal 9 videosunu inceleyin.
