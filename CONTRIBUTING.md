---
ms.openlocfilehash: 469be53e14c42775f21ef1ef815becd5cad03a97
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336717"
---
# <a name="contributing"></a>Katkıda bulunma

.NET belgelerine katkıda bulunma konusundaki ilginiz için teşekkürler!

> Kılavuzumuzu site genelinde bir katkı Kılavuzu 'na taşıma sürecimize ihtiyacımız duyuyoruz.
> Yeni Kılavuzu görmek için [Microsoft docs katkıda bulunan kılavuzuna genel bakış](https://docs.microsoft.com/contribute/)' ı ziyaret edin.

Belge, [.net belge sitesinde](https://docs.microsoft.com/dotnet)barındırılan makalelere ve kod örneklerine katkıda bulunma sürecini ele alır. Katkılarınız, yazım hatalarını düzeltmek gibi basit veya yeni bir makale oluşturmak gibi karmaşık olabilir.

- [DOs ve yapılmaması gerekenler](#dos-and-donts)
- [Katkıda bulunan için işlem](#process-for-contributing)
- [C# Etkileşimli deneyim](#the-c-interactive-experience)
- [Katkıda bulunan lisans sözleşmesi](#contributor-license-agreement)

Bu depo, .NET kavramsal belgelerini içerir. .NET belgeleri sitesi buna ek olarak birden çok depodan oluşturulmuştur:

- [Kod örnekleri ve kod parçacıkları](https://github.com/dotnet/samples) Bu depo için sorunlar ve görevler [DotNet/docs/sorunlar](https://github.com/dotnet/docs/issues)bölümünde izlenir.
- [.NET API başvurusu](https://github.com/dotnet/dotnet-api-docs) Bu depo için sorunlar ve görevler [DotNet/DotNet-api-docs/sorunlar](https://github.com/dotnet/dotnet-api-docs/issues)' de izlenir.
- [.Net COMPILER Platform SDK başvurusu](https://github.com/dotnet/roslyn-api-docs) Bu depoya yönelik sorunlar ve görevler [DotNet/docs/sorunlar](https://github.com/dotnet/docs/issues)bölümünde izlenir.

## <a name="dos-and-donts"></a>DOs ve yapılmaması gerekenler

Aşağıdaki listede .NET belgelerine katkıda bulunurken göz önünde bulundurmanız gereken bazı rehber kurallar gösterilmiştir:

- **YAPMAYIN**: Büyük çekme istekleriyle bizi şaşırtmayın. Uzun vakitler harcamadan önce, izlemeniz gereken yol hakkında bir anlaşmaya varabilmemiz için karşılaştığınız sorunu bildirin ve bir tartışma başlatın. Toplu değişiklikler için çalışmayı daha küçük PR 'ler (en fazla 100 dosya) olarak bölün. Bu kılavuz, çekme isteği aşağıdaki kurallara uyulmazsa önemle önerilir.
- Görevlerle ilgili öneriler için Şu anki [Dallarınızla](https://github.com/dotnet/docs/labels/up-for-grabs) **sorunlarına göz atın** .
- Her görev için bir **PR oluşturun.** Birden çok ilgisiz değişiklik içeren PR 'ler, incelenmek çok daha zordur. Bu, İncelemeleri ve PR 'ler birleştirmeyi geciktirir. Bu kılavuz gözden geçirmeler için de geçerlidir: incelemelerde ilişkisiz değişiklikler öneremiyoruz; topluluğun bu kılavuza bağlı olduğunu soruyoruz.
- Çekme ortamınızdaki çalışmanın net bir **açıklamasını sağlayın.** Nelerin değiştiğini ve neden olduğunu bize bildirin. "Update article.md" öğesinin varsayılan açıklaması gözden geçirenler için yararlı değildir.
- Önceki bir tartışmadan yalnızca stil değişiklikleri için **PR 'ler gönderme.** Bu PR 'ler doğruluk açısından incelenmek için ek süre sürer ve bunları birleştirmek, diğer önemli güncelleştirmelerle birleştirme çakışmalarına neden olur. Tutarlı bir stili takip etmek için çalışıyoruz, ancak diğer görevlerle çalışmayı dengeliyoruz. Makaleler, diğer nedenlerle önemli güncelleştirmeler yaptığımız zaman stil uyumına getirilir.
- [Stil kılavuzunu](./styleguide/template.md) ve [ses ve ton](./styleguide/voice-tone.md) **kılavuzlarını okuyun.** Yeni eklemeler bu yönergeleri izlemelidir.
- **YAPIN**: Makaleler üzerinde çalışmaya başlamadan önce çatalınızda ayrı bir dal oluşturun.
- **YAPIN**: [GitHub Flow iş akışını](https://guides.github.com/introduction/flow/) takip edin.
- **YAPIN**: Katkılarınız hakkında sık sık blog gönderisi yazın, tweet atın veya herhangi bir şekilde haber verin.

Bu yönergeler herkesin süresini dikkate almanıza yardımcı olur. Birçok kişi bu depolara katkıda bulunur. Bu yönergelerin ardından, çekme isteğinizi zamanında incelemenizi ve birleşmemizi kolaylaştırır. Bu uygulamalar, diğer topluluk üyelerinden ve takımımız PR 'ler çakışmaları en aza indirir. Bu yönergeleri takip etmediği PR 'ler, genellikle ABD ve topluluk üyeleri için ek işe neden olur, bu PR 'ler reddedilebilir. Bir özel durum istiyorsanız, bir sorun oluşturarak başlayın.

> Not: bazı konuların Şu anda burada belirtilen tüm yönergeleri ve [Stil kılavuzunu](./styleguide/template.md) takip ettiğini fark edebilirsiniz. Site genelinde tutarlılığı sağlamak adına çalışıyoruz.

## <a name="process-for-contributing"></a>Katkıda bulunan için işlem

[Git ve GitHub.com](https://guides.github.com/activities/hello-world/)'in temel bir şekilde anlaşılmasına ihtiyacınız vardır.

**1. Adım:** Küçük değişiklikler için bu adımı atlayın (örneğin, bir yazım hatası 'u düzelttiğinizde veya belgeler içinde bulduğunuz bir sorunu gidermek için hemen bir çekme isteği açarsanız). Yeni içerik yazmak veya mevcut bir içeriği kapsamlı şekilde düzenlemek istiyorsanız yapmak istediğinizi açıklayan bir [sorun](https://github.com/dotnet/docs/issues) açın.
*Belgeler* klasöründeki içerik, İçindekiler’de (TOC) belirtilen bölümlere ayrılır. İçeriğin bu tablonun neresinde yer alacağını belirtin. Teklifiniz hakkında geri bildirim alın.

veya

Topluluğun katkıda bulunabileceği mevcut sorunlardan birini de seçebilirsiniz. [.Net Community katkıda bulunanlar Için projeler](https://github.com/dotnet/docs/projects/35) , topluluk katkı sağlayanlar için kullanılabilen iş öğelerinin çoğunu listeler. İlgi alanınıza ve ayırmak istediğiniz zamana göre şu sorun kategorileri arasından seçim yapabilirsiniz:

- **Bakım**. Bu kategori; bozuk veya hatalı bağlantıları düzeltmek, eksik kod örneklerini eklemek veya sınırlı içerik sorunlarıyla ilgilenmek gibi oldukça basit katkıları içerir. Bazı durumlarda bu sorunlar, çok sayıda dosyayı ilgilendirebilir. Bu durumda, başlamadan önce bize ne üzerinde çalışmak istediğinizi bildirmelisiniz.

- **İçerik güncelleştirmeleri**. Belge kümesi oldukça büyük olduğundan içerikler kolaylıkla güncelliğini kaybedebiliyor ve düzenlemeler gerekebiliyor. Bunlara ek olarak, çeşitli nedenlerle bazı içerikler yinelenmiş veya hatta Üçlü hale geliştirilmiştir. İçeriğin güncelleştirilmesi, ayrı ayrı konuların güncel tutulmasını sağlamayı veya tekrarı önlemek ve tüm benzersiz içeriğin daha küçük belge kümelerinde saklanmak için bir özellik alanındaki içeriğin düzenlenmesini içerir.

- **Yeni içerik yazma**. Kendi seçtiğiniz bir konu hakkında makale yazmak istiyorsanız bu sorunlar arasında, belge kümemize eklemek istediğimiz konuları bulabilirsiniz. Ancak bir konu üzerinde çalışmaya başlamadan önce bize haber verin. Burada belirtilmemiş bir konuda makale yazmak istiyorsanız bir sorun açın.

Dilerseniz [açık sorunlar](https://github.com/dotnet/docs/issues) listemize bakıp ilginizi çeken konular üzerinde çalışmak üzere gönüllü olabilirsiniz. Katkı için açık olan sorunları [etiketleyerek, for-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) etiketini kullanırız.

**2. Adım:** `dotnet/docs`, `dotnet/samples` veya `dotnet/dotnet-api-docs` depoları çatalla ve yaptığınız değişiklikler için bir dal oluşturun.

Küçük değişiklikler için GitHub 'ın Web arabirimini kullanabilirsiniz. Değiştirmek istediğiniz dosyada **Bu projenin çatalınızda dosyayı Düzenle** ' ye tıklamanız yeterlidir. Değişiklikleri gönderdiğinizde GitHub yeni dalı sizin için oluşturur.

**3. Adım:** Değişiklikleri bu yeni dalda yapın.

Yeni bir konu üzerine yazıyorsanız başlangıç noktası olarak bu [şablon dosyayı](./styleguide/template.md) kullanabilirsiniz. Dosya, yazma yönergelerini içerir ve her bir makale için gerekli olan yazar bilgisi gibi meta verileri açıklar.

1\. adımda makaleniz için belirlenen TOC konumuna karşılık gelen klasöre gidin.
Bu klasör, bu bölümdeki tüm makalelerin Markdown dosyalarını barındırır.
Gerekiyorsa içeriğinize ait dosyaları koyacağınız yeni bir klasör oluşturun. Bu bölümün ana makalesinin adı *index.md*’dir.
Görüntüler ve diğer statik kaynaklar için makalenizin bulunduğu klasör içerisinde *medya* adlı bir alt klasör yoksa yenisini oluşturun. *Medya* klasöründe makale adını taşıyan bir alt klasör oluşturun (dizin dosyası hariç).
Depo kökünün altındaki *örnekler* klasörüne daha büyük örnekler ekleyin.

Doğru Markdown söz dizimini izlediğinize emin olun. Daha fazla bilgi için bkz. [Stil Kılavuzu](./styleguide/template.md).

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

**4. Adım:** `dotnet/docs/master`, `dotnet/dotnet-api-docs/master`veya `dotnet/samples/master`için dalınızdan çekme Isteği (PR) gönderme.

PR 'niz *her zaman* deponun varsayılan dalını hedeflemelidir (bir yayın dalı üzerinde çalışmadığınız müddetçe). DotNet/docs için ana dal varsayılan daldır. Yerelleştirilmiş depolar için, dinamik dal varsayılan bir. DotNet/docs üzerinde canlı dalı hedefleyen bir PR 'yi *asla* açmanız gerekir.

Her bir PR, yalnızca bir sorunu ele almalıdır. PR, bir veya birden fazla dosyayı değiştirebilir. Farklı dosyalardaki birden fazla düzeltmeyle ilgileniyorsanız, ayrı PR’ler göndermeniz tercih edilir.

Çekme isteği mevcut bir sorunu ele alıyorsa, işleme iletisine veya PR açıklamasına `Fixes #Issue_Number` anahtar sözcüğünü ekleyin. Böylece PR birleştirildiğinde sorun otomatik olarak kapatılır. Daha fazla bilgi için bkz. [İşleme iletisi yoluyla sorunları kapatma](https://help.github.com/articles/closing-issues-via-commit-messages/).

.NET ekibi, PR’nizi inceleyecek ve PR’nin onaylanması için yapılması gereken başka güncelleştirme/değişiklik olup olmadığını size bildirecektir.

**5. Adım:** Ekiple konuşulduğu şekilde gerekli güncelleştirmeleri dalınıza uygulayın.

Geri bildirim uygulandığında ve değişikliğiniz onaylandığında bakımcılar, PR’nizi ana dalla birleştirecektir.

Belirli bir temposunda, Ana daldaki tüm işlemeleri canlı dala gönderiyoruz ve sonra https://docs.microsoft.com/dotnet/ katkılarınızı canlı olarak görebileceksiniz.

### <a name="contributing-to-samples"></a>Örneklere katkıda bulunma

Depomuzda bulunan kodlar için şu ayrımı yaparız:

- Örnekler: Okuyucular örnekleri indirebilir ve çalıştırabilir. Örneklerin tümü, tam uygulamalar veya kitaplıklar olmalıdır. Örnek, bir kitaplık oluşturuyorsa bu kitaplık, birim testleri veya okuyucuların kodu çalıştırmasını sağlayan bir uygulama içermelidir.

- Kod parçacıkları: Daha küçük bir kavramı veya görevi betimler. Bunlar derlenebilir, ancak tam uygulamalar olmaları beklenmez.

Tüm kodlar, [dotnet/samples](https://github.com/dotnet/samples) deposunda bulunur. Örnekler klasörünün yapısının belgeler klasörünün yapısıyla eşleştiği bir model üzerinde çalışıyoruz. İzlediğimiz standartlar şunlardır:

- Üst düzey *kod parçacıkları* klasörü, küçük ve odaklanmış örnekleri barındırır.
- API başvuru örnekleri şu düzenin ardından gelen bir klasörde: *parçacıklar/\<language >/api/\<ad alanı >/\<apiname >* .
- Diğer üst düzey klasörler, *belgeler* deposundaki üst düzey klasörlerle eşleşmektedir. Örneğin belgeler deposunda bir *machine-learning/tutorials* klasörü varsa makine öğrenimi öğreticileri *samples/machine-learning/tutorials* klasöründedir.

Ayrıca *temel* ve *standart* klasörlerindeki tüm örnekler, .NET Core tarafından desteklenen tüm platformlarda derlenmeli ve çalışmalıdır. CI derleme sistemimiz bunu zorunlu kılar. Üst düzey *çerçeve* klasörü, yalnızca Windows’ta derlenen ve doğrulanan örnekleri barındırır.

Docs deposu yeni içerik eklediği için bu dizinleri genişletebiliriz. Örneğin, `xamarin-ios` ve `xamarin-android` dizinleri gibi Xamarin dizinleri ekleyeceğiz.

Oluşturduğunuz her bir tam örnekte bir *readme.md* dosyası olmalıdır. Bu dosya, örneğin kısa bir açıklamasını içermelidir (bir veya iki paragraf). *readme.md* dosyanız, okuyuculara bu örneği keşfederek ne öğreneceklerini anlatmalıdır. *readme.md* dosyası ayrıca [.NET belgeleri sitesindeki](https://docs.microsoft.com/dotnet/welcome) yayımlanmış belgeye yönlendiren bir bağlantı da içermelidir.
Depodaki herhangi bir dosyanın bu siteyle eşlenip eşlenmediğini belirlemek için depo yolundaki `/docs` öğesini `https://docs.microsoft.com/dotnet` ile değiştirin.

Konunuzun içinde de örneğe yönlendiren bağlantılar olacaktır. Doğrudan örneğin GitHub’daki klasörüne bağlantı verin.

Daha fazla bilgi için bkz. [Samples Readme](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>Etkileşimli C# deneyimi

C# dilindeki kısa kod örnekleri, tarayıcıda çalışan bir C# örneğini belirtmek için `csharp-interactive` bilgisayar dili etiketini kullanabilir. (Satır içi kod örnekleri `csharp-interactive` etiketini kullanır, kaynaktan dahil olan kod parçacıkları için `code-csharp-interactive` etiketini kullanın.) Bu kod örnekleri, makalede bir kod penceresi ve bir çıkış penceresi görüntüler. Çıkış penceresi, örnek kullanıcı tarafından çalıştırdığında etkileşimli kodun yürütülmesinden ortaya çıkan çıkışları gösterir.

Etkileşimli C# deneyimi, örneklerle çalışma şeklimizi değiştirir. Ziyaretçiler, sonuçları görmek için örneği çalıştırabilirler. Örneğin veya örneğe karşılık gelen metnin çıkış bilgilerini içerip içermeyeceğini belirlemeye yardım eden birkaç etken vardır.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Örnek çalıştırılmadan beklenen çıkışın gösterileceği durumlar

- Yeni başlayanlara yönelik makaleler, okuyucunun kendi sonuçlarıyla beklenen yanıtı kıyaslayabilmesi için çıkış sağlamalıdır.
- Çıkışın konu için önemli olduğu örneklerde bu çıkış gösterilmelidir. Örneğin, biçimlendirilmiş metinle ilgili makalelerde örnek çalıştırılmadan metin biçimi gösterilmelidir.
- Hem örnek hem de beklenen çıkış kısa olduğunda çıkışı göstermek göz önünde bulundurulabilir. Bu, bir miktar zaman tasarrufu sağlar.
- Geçerli kültür veya sabit kültürün çıkışı nasıl etkilediğini açıklayan makalelerde beklenen çıkış açıklanmalıdır. Etkileşimli REPL (Oku Değerlendir Yazdır Döngüsü), Linux tabanlı bir ana bilgisayarda çalışır. Varsayılan kültür ve sabit kültür, farklı işletim sistemlerinde ve makinelerde farklı sonuçlar üretir. Bu makalede Windows, Linux ve Mac sistemlerindeki çıkış açıklanmıştır.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Beklenen çıkışın örneğe eklenmeyeceği durumlar

- Örneğin büyük bir çıkış oluşturduğu makalelerde bu çıkış, açıklamalarda olmamalıdır. Bu, örnek çalıştırıldığında kodu anlaşılmaz hale getirir.
- Örneğin bir konuyu gösterdiği ancak çıkışın konu için önemli olmadığı makalelerde. Örneğin, sorgu söz dizimini açıklamak için bir LINQ sorgusu çalıştıran ve daha sonra tüm öğeleri çıkış koleksiyonunda görüntüleyen kodlar.

## <a name="contributor-license-agreement"></a>Katkıda bulunan lisans sözleşmesi

PR’niz birleştirilmeden önce [.NET Foundation Katılım Lisans Sözleşmesi’ni (CLA)](https://cla.dotnetfoundation.org) imzalamanız gerekir. Bu, .NET Foundation projeleri için tek seferlik bir gereksinimdir. [Katılım Lisans Sözleşmeleri (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) hakkında Wikipedia’dan daha fazla bilgi edinebilirsiniz.

Sözleşme: [net-foundation-contribution-license-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Sözleşmeyi önceden imzalamanız gerekmez. PR’nizin kopyalama, gönderme, çatalını oluşturma işlemlerini her zamanki gibi yapabilirsiniz. PR’niz oluşturulduğunda, bir CLA botu tarafından sınıflandırılır. Değişiklik önemsiz (örneğin, bir typo düzeltildi) ise, çekme isteği `cla-not-required`etiketlenir. Büyük değişikliklerde ise `cla-required` olarak sınıflandırılır. CLA’yı imzaladıktan sonra geçerli ve gelecek tüm çekme istekleri `cla-signed` olarak etiketlenir.
