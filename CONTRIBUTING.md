---
ms.openlocfilehash: e5da9a98e8725880223df3737dc60f773db8d20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79141139"
---
# <a name="contributing"></a>Katkıda bulunma

.NET belgelerine katkıda bulunma konusundaki ilginiz için teşekkürler!

> Yönergelerimizi site çapında bir katkı kılavuzuna taşıma sürecindeyiz.
> Yeni kılavuzu görmek için [Microsoft Dokümanlar katılımcı kılavuzuna genel bakış sayfasını](https://docs.microsoft.com/contribute/)ziyaret edin.

Belge, [.NET dokümantasyon sitesinde](https://docs.microsoft.com/dotnet)barındırılan makalelere ve kod örneklerine katkıda bulunmak için yapılan süreci kapsar. Katkılarınız, yazım hatalarını düzeltmek gibi basit veya yeni bir makale oluşturmak gibi karmaşık olabilir.

- [DOs ve DON'ts](#dos-and-donts)
- [Katkıda bulunmak için süreç](#process-for-contributing)
- [Etkileşimli C# deneyimi](#the-c-interactive-experience)
- [Katılımcı Lisans Sözleşmesi](#contributor-license-agreement)

Bu depo .NET için kavramsal dokümantasyon içerir. .NET dokümantasyon sitesi buna ek olarak birden fazla depodan oluşturulmuştur:

- [Kod örnekleri ve parçacıklar](https://github.com/dotnet/samples) Bu deponun sorunları ve görevleri [dotnet/docs/issues](https://github.com/dotnet/docs/issues)adresinde izlenir.
- [.NET API başvurusu](https://github.com/dotnet/dotnet-api-docs) Bu deponun sorunları ve görevleri [dotnet/dotnet-api-docs/issues](https://github.com/dotnet/dotnet-api-docs/issues)adresinde izlenir.
- [.NET Derleyici Platformu SDK referansı](https://github.com/dotnet/roslyn-api-docs) Bu repo ile ilgili sorunlar ve görevler [dotnet/docs/issues](https://github.com/dotnet/docs/issues)adresinde izlenir.

### <a name="contributing-to-international-content"></a>Uluslararası içeriğe katkıda bulunmak

Machine Translated (MT) içeriğine yapılan katkılar şimdilik kabul edilmemaktadır. MT içeriğinin kalitesini artırmak amacıyla, bir Nöral MT motoruna geçiş yaptık. Nöral MT motorun eğitimi için kullanılan Human Translated (HT) içeriğine katkıları kabul ve teşvik ediyoruz. Yani zaman içinde, HT içeriğine katkıları ht ve MT hem kalitesini artıracaktır. MT konuları, konunun bir bölümünün MT olabileceğini belirten bir feragatnameye sahip olur ve **Edit** düğmesi devre dışı bırakılmış olarak görüntülenmez.

## <a name="dos-and-donts"></a>DOs ve DON'ts

Aşağıdaki listede .NET belgelerine katkıda bulunurken göz önünde bulundurmanız gereken bazı rehber kurallar gösterilmiştir:

- **YAPMAYIN**: Büyük çekme istekleriyle bizi şaşırtmayın. Uzun vakitler harcamadan önce, izlemeniz gereken yol hakkında bir anlaşmaya varabilmemiz için karşılaştığınız sorunu bildirin ve bir tartışma başlatın. Toplu değişiklikler için, çalışmayı daha küçük PR'lere (en fazla 100 dosya) ayırın. Pr aşağıdaki yönergeleri takip etmiyorsa bu kılavuz şiddetle tavsiye edilir.
- **DO** görevleri önerileri için kapmak sorunları için geçerli [kadar](https://github.com/dotnet/docs/labels/up-for-grabs) bakmak.
- **DO** her görev için bir PR oluşturun. Birden çok ilgisiz değişiklik içeren PR'leri gözden geçirmek çok daha zordur. Bu, yorumları ve pr'leri birleştirmeyi geciktirir. Bu kılavuz incelemeler için de geçerlidir: değerlendirmelerde alakasız değişiklikler önermemeye çalışırız; topluluk değerlendirmelerini bu kılavuza uygun hale getirmek istiyoruz.
- **DO** PR iş net bir açıklama sağlar. Bize neyin ve neden değiştiğini söyle. "article.md güncelleştirme" varsayılan açıklaması gözden geçirenler için yararlı değildir.
- **DON'T** Önceden tartışmadan yalnızca stil değişiklikleri için PR göndermeyin. Bu PR'lerin doğruluğu gözden geçirmesi için fazladan zaman ayırın ve bunları birleştirmek genellikle diğer önemli güncelleştirmelerle birleştirme çakışmalarına neden olur. Tutarlı bir stil izleme yönünde çalışıyoruz, ancak bu çalışmayı diğer görevlerle dengeliyoruz. Makaleler, diğer nedenlerle büyük güncellemeler yaptığımızda stil uygunluğuna getirilir.
- **DO** [stil kılavuzu](./styleguide/template.md) ve ses [ve sesi](./styleguide/voice-tone.md) yönergeleri okuyun. Yeni eklemeler bu yönergeleri izlemelidir.
- **YAPIN**: Makaleler üzerinde çalışmaya başlamadan önce çatalınızda ayrı bir dal oluşturun.
- **YAPIN**: [GitHub Flow iş akışını](https://guides.github.com/introduction/flow/) takip edin.
- **YAPIN**: Katkılarınız hakkında sık sık blog gönderisi yazın, tweet atın veya herhangi bir şekilde haber verin.

Bu kurallar herkesin zamanına saygı göstermemize yardımcı olur. Birçok kişi bu depolara katkıda bulunur. Bu yönergeleri izleyerek, pr'ınızı zamanında gözden geçirmemizi ve birleştirmemizi kolaylaştırır. Bu uygulamalar, diğer topluluk üyelerinin ve ekibimizin PR'leri ile çakışmaları en aza indirir. Bu kurallara uymayan PR'ler genellikle bizim ve topluluk üyeleri için ek iş neden olduğundan, bu PR'ler reddedilebilir. Bir özel durum istiyorsanız, bir sorun oluşturarak başlayın.

> Not: Bazı konuların şu anda burada ve [stil kılavuzunda](./styleguide/template.md) belirtilen tüm yönergeleri takip etmediğini fark edebilirsiniz. Site genelinde tutarlılığı sağlamak adına çalışıyoruz.

## <a name="process-for-contributing"></a>Katkıda bulunmak için süreç

[Git ve GitHub.com](https://guides.github.com/activities/hello-world/)temel bir anlayış gerekir.

**Adım 1:** Küçük değişiklikler için bu adımı atlayın (örneğin, yazım hatasını düzeltiyorsanız veya dokümanlarda bulduğunuz bir sorunu gidermek için hemen çekme isteği açıyorsanız). Yeni içerik yazmak veya varolan içeriği gözden geçirmek istiyorsanız, ne yapmak istediğinizi açıklayan bir [sorun](https://github.com/dotnet/docs/issues) açın.
*Belgeler* klasöründeki içerik, İçindekiler’de (TOC) belirtilen bölümlere ayrılır. İçeriğin bu tablonun neresinde yer alacağını belirtin. Teklifiniz hakkında geri bildirim alın.

-veya-

Topluluğun katkıda bulunabileceği mevcut sorunlardan birini de seçebilirsiniz. [.NET Topluluk katılımcıları için projeler,](https://github.com/dotnet/docs/projects/35) topluluk katılımcıları için kullanılabilen iş öğelerinin çoğunu listeler. İlgi alanınıza ve ayırmak istediğiniz zamana göre şu sorun kategorileri arasından seçim yapabilirsiniz:

- **Bakım**. Bu kategori; bozuk veya hatalı bağlantıları düzeltmek, eksik kod örneklerini eklemek veya sınırlı içerik sorunlarıyla ilgilenmek gibi oldukça basit katkıları içerir. Bazı durumlarda bu sorunlar, çok sayıda dosyayı ilgilendirebilir. Bu durumda, başlamadan önce bize ne üzerinde çalışmak istediğinizi bildirmelisiniz.

- **İçerik güncelleştirmeleri**. Belge kümesi oldukça büyük olduğundan içerikler kolaylıkla güncelliğini kaybedebiliyor ve düzenlemeler gerekebiliyor. Buna ek olarak, çeşitli nedenlerden dolayı, bazı içerik çoğaltılmış ve hatta tüçkezlenmiştir. İçeriğin güncelleştirilmesi, ayrı ayrı konuların güncel tutulmasını sağlamayı veya tekrarı önlemek ve tüm benzersiz içeriğin daha küçük belge kümelerinde saklanmak için bir özellik alanındaki içeriğin düzenlenmesini içerir.

- **Yeni içerik yazma**. Kendi seçtiğiniz bir konu hakkında makale yazmak istiyorsanız bu sorunlar arasında, belge kümemize eklemek istediğimiz konuları bulabilirsiniz. Ancak bir konu üzerinde çalışmaya başlamadan önce bize haber verin. Burada belirtilmemiş bir konuda makale yazmak istiyorsanız bir sorun açın.

Dilerseniz [açık sorunlar](https://github.com/dotnet/docs/issues) listemize bakıp ilginizi çeken konular üzerinde çalışmak üzere gönüllü olabilirsiniz. Katkıları için açık sorunları etiketlemek [için up-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) etiketini kullanırız.

**Adım 2:** Fork `dotnet/docs`, `dotnet/samples` `dotnet/dotnet-api-docs` veya gerektiğinde depolar ve değişiklikleriniz için bir dal oluşturun.

Küçük değişiklikler için GitHub'ın web arabirimini kullanabilirsiniz. Değiştirmek istediğiniz **dosyada bu projenin çatalındaki dosyayı edit'i** tıklatmanız yeterlidir. Değişiklikleri gönderdiğinde GitHub sizin için yeni bir şube oluşturur.

**3. Adım:** Değişiklikleri bu yeni dalda yapın.

Yeni bir konu üzerine yazıyorsanız başlangıç noktası olarak bu [şablon dosyayı](./styleguide/template.md) kullanabilirsiniz. Dosya, yazma yönergelerini içerir ve her bir makale için gerekli olan yazar bilgisi gibi meta verileri açıklar.

1. adımda makaleniz için belirlenen TOC konumuna karşılık gelen klasöre gidin.
Bu klasör, bu bölümdeki tüm makalelerin Markdown dosyalarını barındırır.
Gerekiyorsa içeriğinize ait dosyaları koyacağınız yeni bir klasör oluşturun. Bu bölümün ana makalesinin adı *index.md*’dir.
Görüntüler ve diğer statik kaynaklar için makalenizin bulunduğu klasör içerisinde *medya* adlı bir alt klasör yoksa yenisini oluşturun. *Medya* klasöründe makale adını taşıyan bir alt klasör oluşturun (dizin dosyası hariç).
Repo'nun altındaki *örnekler* klasörüne daha büyük örnekler ekleyin.

Doğru Markdown söz dizimini izlediğinize emin olun. Daha fazla bilgi için [stil kılavuzuna](./styleguide/template.md)bakın.

### <a name="example-structure"></a>Örnek yapı

```
docs
  /about
  /core
    /porting
      porting-overview.md
      /media
        /porting-overview
            portability_report.png
```

**Adım 4:** Şubenizden çekme isteği (PR) `dotnet/docs/master`ile `dotnet/dotnet-api-docs/master`' `dotnet/samples/master`veya .

PR'ınız *her zaman* deponun varsayılan dalını hedeflemelidir (bir sürüm dalı üzerinde çalışmıyorsanız). dotnet/docs için ana dal varsayılan dalıdır. Yerelleştirilmiş depolar için canlı dal varsayılan olandır. Dotnet/docs'ta canlı şubeyi hedefleyen bir pr'ı *asla* açmamalısınız.

Her bir PR, yalnızca bir sorunu ele almalıdır. PR, bir veya birden fazla dosyayı değiştirebilir. Farklı dosyalardaki birden fazla düzeltmeyle ilgileniyorsanız, ayrı PR’ler göndermeniz tercih edilir.

PR'ınız varolan bir sorunu ele `Fixes #Issue_Number` alıyorsa, anahtar kelimeyi iletme iletisine veya PR açıklamasına ekleyin. Böylece PR birleştirildiğinde sorun otomatik olarak kapatılır. Daha fazla bilgi için bkz. [İşleme iletisi yoluyla sorunları kapatma](https://help.github.com/articles/closing-issues-via-commit-messages/).

.NET ekibi, PR’nizi inceleyecek ve PR’nin onaylanması için yapılması gereken başka güncelleştirme/değişiklik olup olmadığını size bildirecektir.

**5. Adım:** Ekiple konuşulduğu şekilde gerekli güncelleştirmeleri dalınıza uygulayın.

Geri bildirim uygulandığında ve değişikliğiniz onaylandığında bakımcılar, PR’nizi ana dalla birleştirecektir.

Belirli bir cadence günü, biz canlı şube içine ana şube tüm taahhütleri itmek ve https://docs.microsoft.com/dotnet/daha sonra katkıcanlı görmek mümkün olacak .

### <a name="contributing-to-samples"></a>Örneklere katkıda bulunma

Depomuzda bulunan kodlar için şu ayrımı yaparız:

- Örnekler: Okuyucular örnekleri indirebilir ve çalıştırabilir. Örneklerin tümü, tam uygulamalar veya kitaplıklar olmalıdır. Örnek, bir kitaplık oluşturuyorsa bu kitaplık, birim testleri veya okuyucuların kodu çalıştırmasını sağlayan bir uygulama içermelidir.

- Kod parçacıkları: Daha küçük bir kavramı veya görevi betimler. Bunlar derlenebilir, ancak tam uygulamalar olmaları beklenmez.

Tüm kodlar, [dotnet/samples](https://github.com/dotnet/samples) deposunda bulunur. Örnekler klasörünün yapısının belgeler klasörünün yapısıyla eşleştiği bir model üzerinde çalışıyoruz. İzlediğimiz standartlar şunlardır:

- Üst düzey *kod parçacıkları* klasörü, küçük ve odaklanmış örnekleri barındırır.
- API başvuru örnekleri bu deseni izleyen bir klasörde olmuştur: *\<snippets/ dil>/api/\<namespace>/\<apiname>*.
- Diğer üst düzey klasörler, *belgeler* deposundaki üst düzey klasörlerle eşleşmektedir. Örneğin belgeler deposunda bir *machine-learning/tutorials* klasörü varsa makine öğrenimi öğreticileri *samples/machine-learning/tutorials* klasöründedir.

Ayrıca *temel* ve *standart* klasörlerindeki tüm örnekler, .NET Core tarafından desteklenen tüm platformlarda derlenmeli ve çalışmalıdır. CI derleme sistemimiz bunu zorunlu kılar. Üst düzey *çerçeve* klasörü, yalnızca Windows’ta derlenen ve doğrulanan örnekleri barındırır.

Doküman deposu yeni içerik ekledikçe bu dizinleri genişletebiliriz. Örneğin, Xamarin dizinleri, gibi `xamarin-ios` `xamarin-android` ve dizinler eklersiniz.

Oluşturduğunuz her bir tam örnekte bir *readme.md* dosyası olmalıdır. Bu dosya, örneğin kısa bir açıklamasını içermelidir (bir veya iki paragraf). *readme.md* dosyanız, okuyuculara bu örneği keşfederek ne öğreneceklerini anlatmalıdır. *readme.md* dosyası ayrıca [.NET belgeleri sitesindeki](https://docs.microsoft.com/dotnet/welcome) yayımlanmış belgeye yönlendiren bir bağlantı da içermelidir.
Depodaki herhangi bir dosyanın bu siteyle eşlenip eşlenmediğini belirlemek için depo yolundaki `/docs` öğesini `https://docs.microsoft.com/dotnet` ile değiştirin.

Konunuzun içinde de örneğe yönlendiren bağlantılar olacaktır. Doğrudan örneğin GitHub’daki klasörüne bağlantı verin.

Daha fazla bilgi için [Örnekler Readme'a](https://github.com/dotnet/samples/blob/master/README.md)bakın.

## <a name="the-c-interactive-experience"></a>Etkileşimli C# deneyimi

C# dilindeki kısa kod örnekleri, tarayıcıda çalışan bir C# örneğini belirtmek için `csharp-interactive` bilgisayar dili etiketini kullanabilir. (Satır altı kod `csharp-interactive` örnekleri, kaynaktan alınan parçacıklar için `code-csharp-interactive` etiketi kullanır.) Bu kod örnekleri makalede bir kod penceresi ve çıktı penceresi görüntüler. Çıkış penceresi, örnek kullanıcı tarafından çalıştırdığında etkileşimli kodun yürütülmesinden ortaya çıkan çıkışları gösterir.

Etkileşimli C# deneyimi, örneklerle çalışma şeklimizi değiştirir. Ziyaretçiler, sonuçları görmek için örneği çalıştırabilirler. Örneğin veya örneğe karşılık gelen metnin çıkış bilgilerini içerip içermeyeceğini belirlemeye yardım eden birkaç etken vardır.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Örnek çalıştırılmadan beklenen çıkışın gösterileceği durumlar

- Yeni başlayanlara yönelik makaleler, okuyucunun kendi sonuçlarıyla beklenen yanıtı kıyaslayabilmesi için çıkış sağlamalıdır.
- Çıkışın konu için önemli olduğu örneklerde bu çıkış gösterilmelidir. Örneğin, biçimlendirilmiş metinle ilgili makalelerde örnek çalıştırılmadan metin biçimi gösterilmelidir.
- Hem örnek hem de beklenen çıkış kısa olduğunda çıkışı göstermek göz önünde bulundurulabilir. Bu, bir miktar zaman tasarrufu sağlar.
- Geçerli kültür veya sabit kültürün çıkışı nasıl etkilediğini açıklayan makalelerde beklenen çıkış açıklanmalıdır. Etkileşimli REPL (Oku Değerlendir Yazdır Döngüsü), Linux tabanlı bir ana bilgisayarda çalışır. Varsayılan kültür ve sabit kültür, farklı işletim sistemlerinde ve makinelerde farklı sonuçlar üretir. Bu makalede Windows, Linux ve Mac sistemlerindeki çıkış açıklanmıştır.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Beklenen çıkışın örneğe eklenmeyeceği durumlar

- Örneğin büyük bir çıkış oluşturduğu makalelerde bu çıkış, açıklamalarda olmamalıdır. Bu, örnek çalıştırıldığında kodu anlaşılmaz hale getirir.
- Örneğin bir konuyu gösterdiği ancak çıkışın konu için önemli olmadığı makalelerde. Örneğin, sorgu söz dizimini açıklamak için bir LINQ sorgusu çalıştıran ve daha sonra tüm öğeleri çıkış koleksiyonunda görüntüleyen kodlar.

## <a name="contributor-license-agreement"></a>Katılımcı Lisans Sözleşmesi

PR’niz birleştirilmeden önce [.NET Foundation Katılım Lisans Sözleşmesi’ni (CLA)](https://cla.dotnetfoundation.org) imzalamanız gerekir. Bu, .NET Foundation projeleri için tek seferlik bir gereksinimdir. [Katılım Lisans Sözleşmeleri (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) hakkında Wikipedia’dan daha fazla bilgi edinebilirsiniz.

Sözleşme: [net-foundation-contribution-license-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Sözleşmeyi önceden imzalamanız gerekmez. PR’nizin kopyalama, gönderme, çatalını oluşturma işlemlerini her zamanki gibi yapabilirsiniz. PR’niz oluşturulduğunda, bir CLA botu tarafından sınıflandırılır. Değişiklik önemsizse (örneğin, bir yazım hatası düzelttin), PR `cla-not-required`ile etiketlenir. Büyük değişikliklerde ise `cla-required` olarak sınıflandırılır. CLA’yı imzaladıktan sonra geçerli ve gelecek tüm çekme istekleri `cla-signed` olarak etiketlenir.
