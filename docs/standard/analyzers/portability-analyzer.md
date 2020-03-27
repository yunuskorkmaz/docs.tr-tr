---
title: .NET Taşınabilirlik Analizörü - .NET
description: .NET Core, .NET Standard, UWP ve Xamarin gibi çeşitli .NET uygulamaları arasında kodunuzu ne kadar taşınabilir olduğunu değerlendirmek için .NET Taşınabilirlik Çözümleyicisi aracını nasıl kullanacağınızı öğrenin.
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 397d9f08a0dd28f80d653ac5044d6acfa2418727
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344304"
---
# <a name="the-net-portability-analyzer"></a>.NET Taşınabilirlik Çözümleyicisi

Kitaplıklarınızın çoklu platform desteğini sağlamak ister misiniz? .NET Framework uygulamanızın .NET Core'da çalıştırılabilmesi için ne kadar çalışma gerektiğini görmek ister misiniz? [.NET Taşınabilirlik Çözümleyicisi,](https://github.com/microsoft/dotnet-apiport) derlemeleri analiz eden ve .NET API'leri hakkında, uygulamaların veya kitaplıkların belirtilen hedeflenen .NET platformlarında taşınabilir olması için eksik olan ayrıntılı bir rapor sağlayan bir araçtır. Taşınabilirlik Çözümleyicisi, proje başına bir derlemeyi analiz eden [Visual Studio Extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)ve belirtilen dosyalar veya dizin le derlemeleri analiz eden bir [ApiPort konsol uygulaması](https://aka.ms/apiportdownload)olarak sunulur.

Projenizi .NET Core gibi yeni platformu hedef almak üzere dönüştürdükten sonra, API'lerin <xref:System.PlatformNotSupportedException> özel durumlar ve diğer uyumluluk sorunlarını belirlemek için Roslyn tabanlı [API Çözümleyici aracını](api-analyzer.md) kullanabilirsiniz.

## <a name="common-targets"></a>Ortak hedefler

- [.NET Core](../../core/index.yml): Modüler bir tasarıma sahiptir, yan yana kullanır ve çapraz platform senaryolarını hedefler. Yan yana diğer uygulamaları kırmadan yeni .NET Core sürümlerini benimsemenize olanak tanır. Amacınız uygulamanızı platformlar arası destekleyen .NET Core'a yönlendirmekse, önerilen hedef budur.
- . [NET Standart](../../standard/net-standard.md): Tüm .NET uygulamalarında bulunan .NET Standart API'leri içerir. Amacınız kitaplığınızı tüm .NET destekli platformlarda çalıştırmak sayılsa, bu hedef önerilir.
- [ASP.NET Core](/aspnet/core): .NET Core üzerine inşa edilmiş modern bir web çerçevesi. Amacınız web uygulamanızı birden çok platformu desteklemek için .NET Core'a taşımanızsa, önerilen hedef budur.
- .NET Core + [Platform Uzantıları](../../core/porting/windows-compat-pack.md): .NET Framework kullanılabilir teknolojilerinin çoğunu sağlayan Windows Uyumluluk Paketi'ne ek olarak .NET Core API'leri içerir. Bu, uygulamanızı .NET Framework'den Windows'da .NET Core'a taşımanız için önerilen bir hedeftir.
- .NET Standart + [Platform Uzantıları](../../core/porting/windows-compat-pack.md): .NET Framework kullanılabilir teknolojilerinin çoğunu sağlayan Windows Uyumluluk Paketi'ne ek olarak .NET Standart API'leri içerir. Bu, kitaplığınızı .NET Framework'den .NET Core'a windows'da taşımanız için önerilen bir hedeftir.

## <a name="how-to-use-the-net-portability-analyzer"></a>.NET Taşınabilirlik Analizörü nasıl kullanılır?

Visual Studio'da .NET Taşınabilirlik Çözümleyicisini kullanmaya başlamak için öncelikle [Visual Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)uzantıyı indirmeniz ve yüklemeniz gerekir. Visual Studio 2017 ve sonraki sürümlerinde çalışır. Visual Studio'da **Analyze** > **Taşınabilirlik Çözümleyici** Sayar'ı aracılığıyla yapılandırabilir ve geçerli derlemenizin oluşturduğu platform/sürümle karşılaştırarak taşınabilirlik boşluklarını değerlendirmek istediğiniz .NET platformları/sürümleri olan Hedef Platformlarınızı seçebilirsiniz.

![Taşınabilirlik çözümleyicisinin ekran görüntüsü.](./media/portability-analyzer/portability-screenshot.png)

Ayrıca ApiPort konsol uygulamasını kullanabilirsiniz, [ApiPort deposundan](https://aka.ms/apiportdownload)indirebilirsiniz. Kullanılabilir hedef `listTargets` listesini görüntülemek için komut seçeneğini kullanabilir, ardından `-t` belirtme `--target` veya komut seçeneğini belirterek hedef platformları seçebilirsiniz.

### <a name="analyze-portability"></a>Taşınabilirliği analiz etme
Visual Studio'da projenizin tamamını analiz etmek için **Solution Explorer'da** projenize sağ tıklayın ve **Montaj Taşınabilirliğini Analiz Et'i**seçin. Aksi takdirde, **Çözümle** menüsüne gidin ve **Derleme Taşınabilirliğini Çözümle'yi**seçin. Buradan, projenizin çalıştırılabilir veya DLL'ini seçin.

![Solution Explorer'dan Taşınabilirlik Çözümleyicisinin ekran görüntüsü.](./media/portability-analyzer/portability-solution-explorer.png)

[ApiPort konsol uygulamasını](https://aka.ms/apiportdownload)da kullanabilirsiniz.

- Geçerli dizini çözümlemek için aşağıdaki komutu yazın:`ApiPort.exe analyze -f .`
- .dll dosyalarının belirli bir listesini çözümlemek için aşağıdaki komutu yazın:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Daha `ApiPort.exe -?` fazla yardım almak için çalıştırın

Sahip olduğunuz ve bağlantı noktası olmak istediğiniz ilgili tüm exe ve dll dosyalarını eklemeniz ve uygulamanızın bağlı olduğu ancak sahip olmadığınız ve bağlantı noktası olayamadığınız dosyaları hariç tutmanız önerilir. Bu size en alakalı taşınabilirlik raporu verecektir.

### <a name="view-and-interpret-portability-result"></a>Taşınabilirlik sonucunu görüntüleme ve yorumlama

Raporda yalnızca Hedef Platform tarafından desteklenmeyen API'ler görünür.
Görsel Studio'da çözümlemesi çalıştırdıktan sonra .NET Taşınabilirlik raporu dosya bağlantınızın aç Olduğunu görürsünüz. [ApiPort konsol uygulamasını](https://aka.ms/apiportdownload)kullandıysanız ,.NET Taşınabilirlik raporunuz belirttiğiniz biçimde dosya olarak kaydedilir. Varsayılan değer, geçerli dizininizdeki bir Excel dosyasında (*.xlsx)* olur.

#### <a name="portability-summary"></a>Taşınabilirlik Özeti

![Taşınabilirlik Özeti'nin ekran görüntüsü.](./media/portability-analyzer/api-catalog-portablility-summary.png)

Raporun Taşınabilirlik Özeti bölümü, çalıştırmaya dahil edilen her derleme için taşınabilirlik yüzdesini gösterir. Önceki örnekte, `svcutil` uygulamada kullanılan .NET Framework API'lerinin %71,24'ü .NET Core + Platform Uzantıları'nda mevcuttur. .NET Taşınabilirlik Çözümleyicisi aracını birden çok derlemeye karşı çalıştırdıysanız, her derlemenin Taşınabilirlik Özeti raporunda bir satır olması gerekir.

#### <a name="details"></a>Ayrıntılar

![Taşınabilirlik Ayrıntıları ekran görüntüsü.](./media/portability-analyzer/api-catalog-portablility-details.png)

Raporun **Ayrıntılar** bölümü, seçili **Hedefli Platformlardan**herhangi birinde eksik olan API'leri listeler.

- Hedef türü: tür hedef bir platformdan API eksik
- Hedef üye: yöntem hedef platformdan eksik
- Derleme adı: eksik API'nin yaşadığı .NET Framework derlemesi.
- Seçili Hedef Platformların her biri ".NET Core" gibi bir sütundur: "Desteklenmeyen" değeri, API'nin bu Hedef Platformda desteklenmediğini gösterir.
- Önerilen Değişiklikler: önerilen API veya teknoloji değiştirmek için. Şu anda, bu alan boş veya güncel bir çok API için. API'lerin çok sayıda nedeniyle, bunu sürdürmek için büyük bir sorun var. Müşterilere yararlı bilgiler sağlamak için alternatif çözümler arıyoruz.

#### <a name="missing-assemblies"></a>Eksik Meclisler

![Eksik derlemelerin ekran görüntüsü.](./media/portability-analyzer/api-catalog-missing-assemblies.png)

Raporunda Eksik Derlemeler bölümünü bulabilirsiniz. Bu derlemeler listesi çözümlenmiş derlemeler tarafından başvurulan ve analiz edilmedi söyler. Sahip olduğunuz bir derlemeyse, API düzeyinde ayrıntılı taşınabilirlik raporu alabilmeniz için api taşınabilirlik çözümleyici çalıştırıcıya ekleyin. Üçüncü taraf kitaplığıysa, hedef platformunuzu destekleyen daha yeni bir sürümü olup olmadığını arar. Bu öyleyse, yeni sürüme taşınmayı düşünün. Sonuç olarak, bu listenin uygulamanızın bağlı olduğu tüm üçüncü taraf derlemelerini içermesini ve hedef platformunuzu destekleyen bir sürümü olduğunu onaylamasını beklersiniz.

.NET Taşınabilirlik Çözümleyicisi hakkında daha fazla bilgi için [GitHub belgelerini](https://github.com/Microsoft/dotnet-apiport#documentation) ve [.NET Taşınabilirlik Çözümleyicisi](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Kanal 9 videosuna Kısa Bir Bakış'ı ziyaret edin.
