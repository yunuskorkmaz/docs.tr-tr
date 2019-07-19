---
title: .NET taşınabilirlik Çözümleyicisi-.NET
description: .Net taşınabilirlik Çözümleyicisi aracını kullanarak kodunuzun, .NET Core, .NET Standard, UWP ve Xamarin gibi çeşitli .NET uygulamaları arasında nasıl olduğunu değerlendirmek için nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 07/18/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 433936480aa1181370a6ebc2bd2ba9914a50dfa2
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331735"
---
# <a name="the-net-portability-analyzer"></a>.NET taşınabilirlik Çözümleyicisi

Kitaplıklarınızın çok platformlu desteklemesini sağlamak istiyor musunuz? Uygulamanızı iOS, Android ve Mac için .NET Core, .NET Standard, UWP ve Xamarin dahil diğer .NET uygulamalarıyla ve profilleriyle uyumlu hale getirmek için ne kadar iş gerektiğini görmek ister misiniz? [.Net taşınabilirlik Çözümleyicisi](https://github.com/microsoft/dotnet-apiport) , derlemeleri çözümleyerek programınızın .NET uygulamalarında ne kadar esnek olduğunu gösteren ayrıntılı bir rapor sağlar. Taşınabilirlik Çözümleyicisi, proje başına derlemeyi çözümleyen ve bir [Apiport konsol uygulaması](https://aka.ms/apiportdownload)olarak belirtilen dosyalara veya dizine göre derlemeleri çözümleyen bir [Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)olarak sunulur.

## <a name="common-targets"></a>Ortak hedefler

* [.NET Core](../../core/index.md): Modüler bir tasarıma sahiptir, yan yana ve hedefleri platformlar arası senaryolar kullanır. Yan yana, diğer uygulamaları bozmadan yeni .NET Core sürümlerini benimsemenizi sağlar. Amacınız, uygulamanızın platformlar arası destek ile bağlantı noktası olması durumunda, bu önerilen hedeftir. 
* . [Net standart](../../standard/net-standard.md): Tüm .NET uygulamalarında bulunan .NET Standard API 'Leri içerir. Amacınız, kitaplığınızı tüm .NET tarafından desteklenen platformlarda çalıştırmak istiyorsanız, bu önerilen hedeftir.  
* [ASP.NET Core](/aspnet/core): .NET Core üzerinde oluşturulmuş modern bir Web çerçevesi. Amacınız, Web uygulamanızın birden çok platformu desteklemek üzere .NET Core 'a bağlantı noktası olması durumunda önerilen hedeftir.
* .NET Core + [Platform uzantıları](../../core/porting/windows-compat-pack.md): , Kullanılabilir .NET Framework teknolojilerin çoğunu sağlayan Windows Uyumluluk Paketi 'ne ek olarak .NET Core API 'Lerini de içerir. Bu, uygulamanızın Windows 'da .NET Framework .NET Core 'a taşıma için önerilen bir hedeftir.
* .NET Standard + [Platform uzantıları](../../core/porting/windows-compat-pack.md): , Kullanılabilir .NET Framework birçok teknolojiyi sağlayan Windows Uyumluluk Paketi 'ne ek olarak .NET Standard API 'Leri içerir. Bu, kitaplığınızın .NET Framework Windows üzerinde .NET Core 'a taşıma için önerilen bir hedeftir.

## <a name="how-to-use-the-net-portability-analyzer"></a>.NET taşınabilirlik Çözümleyicisi 'ni kullanma

Visual Studio 'da .NET taşınabilirlik Çözümleyicisi 'ni kullanmaya başlamak için önce uzantıyı [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)indirip yüklemeniz gerekir. Visual Studio 2017 ve sonraki sürümlerinde çalışmaktadır. Bunu, Visual Studio 'da**taşınabilirlik Çözümleyicisi ayarlarını** **Çözümle** > aracılığıyla yapılandırabilir ve platformla karşılaştırarak taşınabilirlik boşluklarını değerlendirmek istediğiniz .net platformları/sürümleri olan hedef Platformlarınızı seçebilirsiniz. geçerli derlemelerinizin oluşturulduğu sürüm.

![Taşınabilirlik ekran görüntüsü](./media/portability-analyzer/portability-screenshot.png)

Ayrıca, ApiPort konsol uygulamasını da kullanabilir, [apiport deposundan](http://aka.ms/apiportdownload)indirebilirsiniz. Kullanılabilir hedef listesini `listTargets` göstermek için komut seçeneğini kullanabilirsiniz, ardından veya `--target` komut seçeneğini belirterek `-t` hedef platformları seçebilirsiniz. 

### <a name="analyze-portability"></a>Taşınabilirliği çözümle
Visual Studio 'daki tüm projenizi çözümlemek için **Çözüm Gezgini** ' de projenize sağ tıklayın ve **derleme taşınabilirliği çözümle**' yi seçin. Aksi takdirde, **Çözümle** menüsüne gidin ve **derleme taşınabilirliği çözümle**' yi seçin. Buradan projenizin yürütülebilir dosyasını veya DLL 'sini seçin.

![Çözüm Gezgini 'ten taşınabilirlik Çözümleyicisi](./media/portability-analyzer/portability-solution-explorer.png)

[Apiport konsol uygulamasını](https://aka.ms/apiportdownload)da kullanabilirsiniz. 

* Geçerli dizini çözümlemek için aşağıdaki komutu yazın:`ApiPort.exe analyze -f .`
* Belirli bir. dll dosyaları listesini analiz etmek için aşağıdaki komutu yazın:`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Daha `ApiPort.exe -?` fazla yardım almak için çalıştırın

Sahip olduğunuz ve bağlantı noktası yapmak istediğiniz tüm ilgili exe ve DLL dosyalarını dahil etmeniz ve uygulamanızın bağlı olduğu dosyaları dışlayamazsınız, ancak bağlantı noktası kullanamazsınız. Bu, size en uygun taşınabilirlik raporu sağlar.  

### <a name="view-and-interpret-portability-result"></a>Taşınabilirlik sonucunu görüntüleme ve yorumlama

Raporda yalnızca bir hedef platform tarafından desteklenmeyen API 'Ler görüntülenir. Analysis 'i Visual Studio 'da çalıştırdıktan sonra, .NET taşınabilirlik rapor dosyası bağlantısı açılır bilgilerinizi görürsünüz. [Apiport konsol uygulamasını](https://aka.ms/apiportdownload)kullandıysanız, .net taşınabilirlik raporunuz belirttiğiniz biçimde bir dosya olarak kaydedilir. Varsayılan değer, geçerli dizininizdeki bir Excel dosyasında ( *. xlsx*) bulunur.

#### <a name="portability-summary"></a>Taşınabilirlik Özeti 

![Taşınabilirlik Özeti](./media/portability-analyzer/portabilitysummary.png)

Raporun taşınabilirlik Özeti bölümünde, çalıştırmada bulunan her derleme için taşınabilirlik yüzdesi gösterilmektedir. Önceki örnekte, `svcutil` uygulamada kullanılan .NET Framework API 'lerinin% 71,24 ' u .NET Core + platform uzantılarında sunulmaktadır. .NET taşınabilirlik Çözümleyicisi aracını birden çok derlemeye karşı çalıştırırsanız, her derlemenin taşınabilirlik Özeti raporunda bir satırı olması gerekir.

#### <a name="details"></a>Ayrıntılar

![Taşınabilirlik ayrıntıları](./media/portability-analyzer/portabilitydetails.png)

Raporun Ayrıntılar bölümünde, hedef platformlardan birinde bulunmayan API 'Ler listelenir. 

- Hedef türü: tür, hedef platformdan eksik API 'ye sahip 
- Hedef üye: Yöntem bir hedef platformda yok 
- Bütünleştirilmiş kod adı: eksik API 'nin üzerinde bulunduğu .NET Framework derlemesi. 
- Seçili hedef platformların her biri, ".NET Core" gibi bir sütunlardır: "Desteklenmiyor" değeri, API 'nin bu hedef platformda desteklenmediği anlamına gelir. 
- Önerilen değişiklikler: olarak değiştirilecek önerilen API veya teknoloji. Şu anda, çok sayıda API için bu alan boş veya güncel değil. Çok sayıda API nedeniyle, bunu tutmanın büyük bir zorluğu vardır. Müşterilere yararlı bilgiler sağlamak için alternatif çözümlere bakıyoruz.

#### <a name="missing-assemblies"></a>Eksik derlemeler

![Taşınabilirlik ayrıntıları](./media/portability-analyzer/missingassemblies.png)

Raporunuzda eksik derlemeler bölümünü bulabilirsiniz. Bu derleme listesine çözümlenen derlemeleriniz tarafından başvurulduğunu ve çözümlenmemiş olduğunu söyler. Sahip olduğunuz bir derlemedir, API seviyesi ayrıntılı taşınabilirlik raporu alabilmek için API taşınabilirlik Çözümleyicisi ' ni çalıştırın. Üçüncü taraf kitaplığı ise, hedef platformunuzu destekleyen daha yeni bir sürüme sahip olup olmadığını arar. Öyleyse, daha yeni sürüme geçmeyi göz önünde bulundurun. Sonuç olarak, bu listenin, uygulamanızın bağımlı olduğu tüm üçüncü taraf derlemelerini içermesi ve hedef platformunuzu destekleyen bir sürüme sahip olduklarını teyit etmeniz gerekir.  

.NET taşınabilirlik Çözümleyicisi hakkında daha fazla bilgi için [GitHub belgelerini](https://github.com/Microsoft/dotnet-apiport#documentation) ziyaret edin ve [.net taşınabilirlik Çözümleyicisi](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Kanal 9 videosunu inceleyin.
