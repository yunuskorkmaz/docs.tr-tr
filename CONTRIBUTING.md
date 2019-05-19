---
ms.openlocfilehash: 21266130bd44d45d03f85cdeee9480b7a9944b55
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876941"
---
# <a name="contributing"></a>Katkıda bulunan

.NET belgeleri için katkıda bulunan İlginiz için teşekkür ederiz!

> Bir site genelinde katkı kılavuzunu koşullarımıza geçme işleminde duyuyoruz. 
> Yeni bir kılavuz için ziyaret edin [Microsoft Docs katkıda bulunan Kılavuzu Genel Bakış](https://docs.microsoft.com/contribute/).

Belge makaleleri ve barındırılan kod örnekleri katkıda bulunmak için işlem içermektedir [.NET belgeler sitesinde](https://docs.microsoft.com/dotnet). Katkılar, yazım düzeltmeleri kadar basit veya yeni makaleler gibi karmaşık olabilir.

* [Katkıda bulunmak için işlem](#process-for-contributing)
* [C# Etkileşimli deneyim](#the-c-interactive-experience)
* [Gerekenler ve yapılmaması gerekenler](#dos-and-donts)
* [Katkıda bulunan lisans sözleşmesi](#contributor-license-agreement)

Bu depo, .NET için kavramsal belgelerde içerir. .NET belgeleri sitesini Bunun yanı sıra birden çok deposu oluşturulur:

- [Kod örnekleri ve kod parçacıkları](https://github.com/dotnet/samples)
- [API başvurusu](https://github.com/dotnet/dotnet-api-docs)
- [.NET derleyici Platformu SDK başvurusu](https://github.com/dotnet/roslyn-api-docs)

Sorunlar ve bu depolar için görevleri buraya izlenir.

## <a name="process-for-contributing"></a>Katkıda bulunmak için işlem

Temel bir anlayış ihtiyacınız [Git ve GitHub.com](https://guides.github.com/activities/hello-world/).

**1. adım:** (Örneğin, yazım hatası düzeltme veya hemen belgelere bulduğunuz bir sorunu gidermek için bir çekme isteği açma) küçük değişiklikler için bu adımı atlayın. Yeni içerik yazma veya var olan içeriğin tamamen düzeltilmesi ilgileniyorsanız, açık bir [sorunu](https://github.com/dotnet/docs/issues) açıklayan ne yapmak istiyorsunuz.
İçindeki içeriği **docs** klasörü, tablo, içeriği (İçindekiler tablosunda) yansıtılır bölümlere düzenlenir. Konunun TOC'de nerede yer alır tanımlayın. Teklifiniz hakkında geri bildirim alın.

-veya-

Ayrıca, mevcut sorunları için hangi topluluk Katkıları davetlidir da tercih edebilirsiniz. [Projeler .NET topluluğa katkıda bulunanlar için](https://github.com/dotnet/docs/projects/35) birçok topluluğa katkıda bulunanlar için kullanılabilir olan iş öğelerini listeler. İlgi alanlarına ve taahhüt düzeyine bağlı olarak, aşağıdaki kategorilerde sorunlar arasından seçim yapabilirsiniz:

- **Bakım**. Bu kategori, bozuk ya da yanlış bağlantıları çözme, eksik kod örnekleri ekleyerek veya adresleme içerik sorunları sınırlı gibi oldukça basit Katkıları içerir. Bazı durumlarda, bu sorunları çok sayıda dosya ile ilgili. Bu durumda, başlamadan önce üzerinde çalışmak istiyorsanız bize bilmeniz gerekir.

- **İçerik güncelleştirmeleri**. Belge kümesinin enormity göz önünde bulundurulduğunda, içeriği kolayca güncel olmayan hale gelir ve düzeltme gerektirir. Ayrıca, neden çeşitli içerikler yinelenen veya bırakıldığı bile triplicated. İçeriği güncelleştirme içerir tek tek ilgili konulara çoğaltma ortadan kaldırmak ve tüm benzersiz içerik daha küçük belgelerinde korunmasını sağlamak için özellik alanında geçerli ya da düzeltme içerik olmasını sağlamaktan ayarlayın.

- **Yeni içerik yazma**. Kendi konu yazmak istiyorsanız, bu sorunları biliyoruz ki belge kümemiz eklemek istediğiniz konuları listeler. Bir konu, ancak çalışmaya başlamadan önce bunu bize bildirin. Burada listelenmeyen bir konu yazılırken ilgileniyorsanız, bir sorun açın. 

Ayrıca bakabilirsiniz bizim [açık sorun](https://github.com/dotnet/docs/issues) listelemek ve ilgilendiğiniz olanları üzerinde çalışılacak volunteer. Kullandığımız [yukarı-için-Dallarınızla](https://github.com/dotnet/docs/labels/up-for-grabs) etiketi sorunları katkısı için açık etiketi. 

**2. adım:** Çatal `dotnet/docs`, `dotnet/samples` veya `dotnet/dotnet-api-docs` depoları olarak gerekli ve değişikliklerinizin bir dal oluşturun.

Küçük değişiklikler için GitHub'ın web arabirimi kullanabilirsiniz. Tıklamanız yeterlidir **çatalınızı bu projenin dosyayı düzenleyin** değiştirmek için istediğiniz dosya çubuğunda. Değişiklikleri gönderdiğinizde GitHub yeni bir dal oluşturur.

**3. adım:** Bu yeni dalda değişiklikleri yapın.

Yeni bir konu varsa bunu kullanabilirsiniz [şablon dosyası](./styleguide/template.md) , başlangıç noktası olarak. Bu yazma yönergeleri içerir ve ayrıca Yazar bilgileri gibi her bir makaleyi için gerekli meta veriler açıklanmaktadır.

1. adımda makale için belirlenen TOC konuma karşılık gelen klasörüne gidin.
Bu klasör için bu bölümdeki tüm makaleleri Markdown dosyalarını içerir.
Gerekirse, içerik için dosyaları yerleştirmek için yeni bir klasör oluşturun. Bu bölüm için ana makale adlı *index.md*.
Görüntüleri ve diğer statik kaynaklar için adında bir alt klasör oluşturmak **medya** zaten yoksa, makale içeren klasörü içinde. İçinde **medya** klasöründe (dizin dosyası dışında) makale ada sahip bir alt klasör oluşturun.
Daha büyük örnek içeren *örnekleri* klasör deponun kök altında.

Uygun Markdown söz dizimini takip ettiğinizden emin olun. Daha fazla bilgi için [Stil Kılavuzu](./styleguide/template.md).

### <a name="example-structure"></a>Örnek yapısı

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

**4. adım:** Bir çekme isteği (PR) için kendi dalınızdaki gönderme `dotnet/docs/master`.

Çekme isteğiniz gereken *her zaman* ana dala hedefleyin. Yapmanız gerekenler *hiçbir zaman* Canlı dala hedefleyen bir PR açın.

Her çekme isteği, genellikle aynı anda bir sorun gidermelidir. Çekme isteği, bir veya birden çok dosyalarda değişiklik yapabilir. Farklı dosya çubuğunda birden çok düzeltmesi ele alan ise ayrı bir PR tercih edilir.

Çekme isteğiniz var olan bir sorunu ele alıyor mu yoksa ekleyin `Fixes #Issue_Number` anahtar sözcüğü bir işleme iletisi veya çekme isteği açıklaması. Çekme isteği birleştirilirken bu şekilde, sorunu otomatik olarak kapatılır. Daha fazla bilgi için [işleme iletileri aracılığıyla sorunlarına kapatma](https://help.github.com/articles/closing-issues-via-commit-messages/).

.NET ekibi, çekme isteği gözden geçirin ve onaylayın için gerekli diğer güncelleştirmeleri/değişiklikler olup olmadığını size bildirmek.

**5. adım:** Gerekli güncelleştirmeleri dalınızda ekiple açıklandığı gibi olun.

Maintainers Çekme geri bildirim uygulandıktan sonra değişiklik onaylandıktan ana dal ile birleştirilecek.

Belirli bir bir temposu üzerinde biz tüm işlemeleri ana daldan Canlı dalına gönderin ve ardından, Canlı katkılarınız görmek mümkün olacaktır https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Örneklerine katkıda bulunan

Depomuzda bulunan kodu aşağıdaki ayrım yapmaya ediyoruz:

- Örnekler: okuyucular indirebilir ve bunları örnekleri çalıştırabilir. Tüm örnekleri eksiksiz uygulamaları ya da kitaplıkları olmalıdır. Örnek, bir kitaplık oluşturur. Burada, birim testleri veya okuyucuların kodu çalıştırmasına olanak sağlayan bir uygulama içermelidir.

- kod parçacıkları: daha küçük bir kavram ya da görev gösterilmektedir. Derlenmesi ancak eksiksiz uygulamaları olması amaçlanmamıştır.

Tüm Canlı kod [dotnet/samples](https://github.com/dotnet/samples) depo. Bizim örnek klasör yapısını bizim docs klasör yapısını eşleştiği bir modele geçiş çalışıyoruz. Sizinle standartları şunlardır:

- En üst düzey *parçacıkları* klasörü, küçük, odaklanmış örnekleri için kod parçacıkları içerir.
- API başvuru örnekleri, bu düzen aşağıdaki klasöründe yapıldı: *parçacıkları /\<dil > /api/\<ad > /\<apiname >*.
- Üst düzey klasörler, diğer üst düzey klasörler eşleşen *docs* depo. Örneğin belge deposu olan bir *machine-learning/öğreticileri* klasörü ve machine learning öğreticileri örnekleri olan *samples/machine-learning/öğreticileri* klasör.

Ayrıca, tüm örnekleri altında *çekirdek* ve *standart* klasörleri oluşturun ve .NET Core tarafından desteklenen tüm platformlarda çalıştırın. CI derleme sistemimiz, zorlar. En üst düzey *framework* klasörü, yalnızca oluşturulan ve Windows üzerinde doğrulanmış örnekleri içerir.

Yeni içerik belge deposu ekler gibi Biz bu dizinler genişleyebilir. Örneğin, Xamarin dizinleri gibi ekleyeceğiz `xamarin-ios` ve `xamarin-android` dizinleri.

Oluşturduğunuz her tam bir örnek içermesi gereken bir *readme.md* dosya. Bu dosya, örnek (bir veya iki paragraf) kısa bir açıklamasını içermelidir. *Readme.md* okuyucuların ne bunlar Bu örneği araştırarak öğreneceksiniz söyleyecektir. *Readme.md* dosya da içermelidir belgenin canlı bağlantı üzerinde [.NET belgeler sitesinde](https://docs.microsoft.com/dotnet/welcome).
Burada belirli bir dosya deposu olarak o siteye eşler belirlemek için değiştirme `/docs` ile depo yolu içinde `https://docs.microsoft.com/dotnet`.

Konu başlığınız örnek bağlantılarını da içerir. GitHub üzerinde örnek kullanıcının klasörüne doğrudan bağlayın.

Daha fazla bilgi için [örnekleri Benioku](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>C# Etkileşimli deneyim

Kod örnekleri kısa C# kullanabilirsiniz `csharp-interactive` belirtmek için dil etiketi bir C# tarayıcıda çalışan bir örnek. (Satır içi kod örnekleri kullan `csharp-interactive` kaynak, içerdiği parçacıkları kullanmak için etiketi `code-csharp-interactive` etiketi.) Bu kod örnekleri, makaledeki bir kod ve bir çıkış penceresinde görüntüler. Çıkış penceresi kullanıcı örneği çalıştırıldıktan sonra gelen etkileşimli kod yürütme herhangi bir çıkış görüntüler. 

C# Etkileşimli deneyim değişiklikleri örnekleri ile nasıl çalışıyoruz. Sonuçları görmek için örnek ziyaretçiler çalıştırabilirsiniz. Bir dizi etkene ilgili metin ve örnek çıktı hakkında bilgi içermelidir, belirlemek.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Ne zaman örneği çalıştırmadan beklenen çıktıyı görüntüleme

- Okuyucular beklenen yanıt iş çıktısını karşılaştırabilmeniz makaleleri yeni başlayanlar için hedeflenen çıkış sağlamanız gerekir.
- Çıkış konuya integral olduğu örnekleri bu çıkışı görüntülemelidir. Örneğin, biçimlendirilmiş metin makalelerde, örneği çalıştırmadan metin biçimi göstermelidir.
- Hem örnek ve beklenen çıktıyı olduğunda kısa çıktısını gösteren göz önünde bulundurun. Bu işlem biraz zaman kaydeder.
- Nasıl geçerli kültürün veya sabit kültür etkileyen çıkış açıklayan makaleler, beklenen çıktıyı açıklayan. Linux tabanlı bir konakta etkileşimli REPL (Read değerlendirmek yazdırma döngüsü) çalıştırır. Varsayılan kültürü ve sabit kültür, farklı işletim sistemleri ve makineler üzerinde farklı bir çıkış üretir. Makale Windows, Linux ve Mac sistemlerinde çıkış açıklayan.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Beklenen çıktıyı örnekten hariç tutmak ne zaman 

- Burada örnek daha büyük bir çıkış oluşturur makalelerde, yorumlarda içermemelidir. Örneği çalıştırıldıktan sonra kodu gizler.
- Makaleler burada örnek bir konu gösterir, ancak çıkış anlamak için tam sayı değil. Örneğin, sorgu söz dizimi açıklamak ve ardından çıkış koleksiyondaki her öğe görüntülemek için bir LINQ Sorgu çalışan kod.

## <a name="dos-and-donts"></a>Gerekenler ve yapılmaması gerekenler

Aşağıdaki liste .NET belgelerine katkıda bulunan, dikkat etmeniz gereken bazı temel kuralları gösterir:

- **Yoksa** bize bulunan büyük çekme istekleri beklenmedik. Bunun yerine, bir sorunu oluşturun ve büyük miktarda zaman yatırım önce bir yönü kabul edebilir, böylece bir tartışma başlatın.
- **YAPMAK** okuma [Stil Kılavuzu](./styleguide/template.md) ve [ses ve sesi](./styleguide/voice-tone.md) yönergeleri.
- **YAPMAK** kullanın [şablon](./styleguide/template.md) dosyası iş başlangıç noktası olarak.
- **YAPMAK** makalelerde çalışmaya başlamadan önce çatalınızdaki ayrı bir dal oluşturun.
- **YAPMAK** izleyin [GitHub akışı iş akışı](https://guides.github.com/introduction/flow/).
- **YAPMAK** blog ve tweet (veya ne olursa olsun) Katkılarınızı, sık!

> Not: konuların bazıları burada belirtilen şu anda tüm yönergeleri izleyerek ve üzerinde olduğunu fark edebilirsiniz [Stil Kılavuzu](./styleguide/template.md) de. Site genelinde tutarlılık elde etmeye yönelik çalışıyoruz. Listesini kontrol edin [açık sorun](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) biz şu anda bu belirli bir hedef için takip ettiğiniz.

## <a name="contributor-license-agreement"></a>Katkıda bulunan lisans sözleşmesi

Oturum açmanız gerekir [.NET Foundation katılım Lisans Sözleşmesi (CLA)](https://cla.dotnetfoundation.org) Çekme isteğiniz birleştirilmeden önce. Bu, .NET Foundation projeleri için tek seferlik bir gereksinimdir. Daha fazla bilgi edinebilirsiniz [katkı lisans sözleşmeleri'ni (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) wikipedia.

Sözleşme: [net-foundation-katkı-lisans-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Ön sözleşme imzalayan gerekmez. Kopyalama, çatalı ve her zaman olduğu gibi çekme isteği gönderin. Çekme isteğiniz oluşturulduğunda, CLA botu tarafından sınıflandırılır. Değişiklik Önemsiz değilse (örneğin, bir yazım yanlışı sabit), çekme isteği ile etiketlenir sonra `cla-not-required`. Aksi takdirde olarak sınıflandırılır `cla-required`. CLA imzalandıktan sonra güncel ve gelecekteki tüm çekme isteklerini olarak etiketlenmiştir `cla-signed`.
