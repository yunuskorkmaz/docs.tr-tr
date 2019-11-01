---
ms.openlocfilehash: 25615dd43f1ae4f56c7bced7f79a0612093a21fb
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191687"
---
# <a name="contributing"></a>Bulunan

.NET belgelerine katkıda bulunmak için ilgilendiğiniz için teşekkür ederiz!

> Kılavuzumuzu site genelinde bir katkı Kılavuzu 'na taşıma sürecimize ihtiyacımız duyuyoruz.
> Yeni Kılavuzu görmek için [Microsoft docs katkıda bulunan kılavuzuna genel bakış](https://docs.microsoft.com/contribute/)' ı ziyaret edin.

Belge, [.net belge sitesinde](https://docs.microsoft.com/dotnet)barındırılan makalelere ve kod örneklerine katkıda bulunma sürecini ele alır. Katkılar, yazım hatası düzeltmeleri kadar basit veya yeni makale olarak karmaşık olabilir.

- [DOs ve yapılmaması gerekenler](#dos-and-donts)
- [Katkıda bulunan için işlem](#process-for-contributing)
- [C# Etkileşimli deneyim](#the-c-interactive-experience)
- [Katkıda bulunan lisans sözleşmesi](#contributor-license-agreement)

Bu depo, .NET kavramsal belgelerini içerir. .NET belgeleri sitesi buna ek olarak birden çok depodan oluşturulmuştur:

- [Kod örnekleri ve kod parçacıkları](https://github.com/dotnet/samples)  
    Bu depo için sorunlar ve görevler [DotNet/docs/sorunlar](https://github.com/dotnet/docs/issues)bölümünde izlenir.
- [.NET API başvurusu](https://github.com/dotnet/dotnet-api-docs)  
    Bu depo için sorunlar ve görevler [DotNet/DotNet-api-docs/sorunlar](https://github.com/dotnet/dotnet-api-docs/issues)' de izlenir.
- [.NET Compiler Platform SDK başvurusu](https://github.com/dotnet/roslyn-api-docs)  
    Bu depoya yönelik sorunlar ve Taks, [DotNet/docs/sorunlar](https://github.com/dotnet/docs/issues)bölümünde izlenir.

## <a name="dos-and-donts"></a>DOs ve yapılmaması gerekenler

Aşağıdaki listede, .NET belgelerine katkıda bulunmak için göz önünde bulundurmanız gereken bazı temel kurallar gösterilmektedir:

- Büyük çekme istekleri konusunda **sürmeyin** . Bunun yerine bir sorun oluşturup bir tartışma başlatın, böylece büyük bir süre yatırmadan önce bir yönü kabul edebilirsiniz. Toplu değişiklikler için çalışmayı daha küçük PR 'ler (en fazla 100 dosya) olarak bölün. Bu kılavuz, çekme isteği aşağıdaki kurallara uyulmazsa önemle önerilir.
- Görevlerle ilgili öneriler için Şu anki [Dallarınızla](https://github.com/dotnet/docs/labels/up-for-grabs) **sorunlarına göz atın** .
- Her görev için bir **PR oluşturun.** Birden çok ilgisiz değişiklik içeren PR 'ler, incelenmek çok daha zordur. Bu, İncelemeleri ve PR 'ler birleştirmeyi geciktirir. Bu kılavuz gözden geçirmeler için de geçerlidir: incelemelerde ilişkisiz değişiklikler öneremiyoruz; topluluğun bu kılavuza bağlı olduğunu soruyoruz.
- Çekme ortamınızdaki çalışmanın net bir **açıklamasını sağlayın.** Nelerin değiştiğini ve neden olduğunu bize bildirin. "Update article.md" öğesinin varsayılan açıklaması gözden geçirenler için yararlı değildir.
- Önceki bir tartışmadan yalnızca stil değişiklikleri için **PR 'ler gönderme.** Bu PR 'ler doğruluk açısından incelenmek için ek süre sürer ve bunları birleştirmek, diğer önemli güncelleştirmelerle birleştirme çakışmalarına neden olur. Tutarlı bir stili takip etmek için çalışıyoruz, ancak diğer görevlerle çalışmayı dengeliyoruz. Makaleler, diğer nedenlerle önemli güncelleştirmeler yaptığımız zaman stil uyumına getirilir. 
- [Stil kılavuzunu](./styleguide/template.md) ve [ses ve ton](./styleguide/voice-tone.md) **kılavuzlarını okuyun.** Yeni eklemeler bu yönergeleri izlemelidir.
- Makaleler üzerinde çalışmadan önce çatalınızda ayrı bir **dal oluşturun.**
- [GitHub Flow iş akışını](https://guides.github.com/introduction/flow/) **izleyin.**
- **Web günlüğü** ve Tweet (veya herhangi bir) katkılarınız hakkında sık sık!

Bu yönergeler herkesin süresini dikkate almanıza yardımcı olur. Birçok kişi bu depolara katkıda bulunur. Bu yönergelerin ardından, çekme isteğinizi zamanında incelemenizi ve birleşmemizi kolaylaştırır. Bu uygulamalar, diğer topluluk üyelerinden ve takımımız PR 'ler çakışmaları en aza indirir. Bu yönergeleri takip etmediği PR 'ler, genellikle ABD ve topluluk üyeleri için ek işe neden olur, bu PR 'ler reddedilebilir. Bir özel durum istiyorsanız, bir sorun oluşturarak başlayın.

> Not: bazı konuların Şu anda burada belirtilen tüm yönergeleri ve [Stil kılavuzunu](./styleguide/template.md) takip ettiğini fark edebilirsiniz. Site genelinde tutarlılık elde etmek için çalışıyoruz.

## <a name="process-for-contributing"></a>Katkıda bulunan için işlem

[Git ve GitHub.com](https://guides.github.com/activities/hello-world/)'in temel bir şekilde anlaşılmasına ihtiyacınız vardır.

**1. Adım:** Küçük değişiklikler için bu adımı atlayın (örneğin, bir yazım hatası 'u düzelttiğinizde veya belgeler içinde bulduğunuz bir sorunu gidermek için hemen bir çekme isteği açarsanız). Yeni içerik yazmak veya var olan içerikleri kapsamlı olarak yeniden gözden aktarmak istiyorsanız, ne yapmak istediğinizi açıklayan bir [sorun](https://github.com/dotnet/docs/issues) açın.
*Docs* klasörünün içindeki Içerikler, içindekiler tablosuna (TOC) yansıtılan bölümler halinde düzenlenmiştir. Konunun TOC 'de nerede olacağını tanımlayın. Teklifiniz hakkında geri bildirim alın.

veya

Ayrıca, topluluk katkılarına hoş geldiniz mevcut sorunlarından da seçim yapabilirsiniz. [.Net Community katkıda bulunanlar Için projeler](https://github.com/dotnet/docs/projects/35) , topluluk katkı sağlayanlar için kullanılabilen iş öğelerinin çoğunu listeler. İlgi alanlarınıza ve taahhüt düzeyine bağlı olarak, aşağıdaki kategorilerdeki sorunlardan seçim yapabilirsiniz:

- **Bakım**. Bu kategori, bozuk veya hatalı bağlantıları düzeltme, eksik kod örneklerini ekleme veya sınırlı içerik sorunlarını giderme gibi oldukça basit katkıları içerir. Bazı durumlarda bu sorunlar çok sayıda dosya olabilir. Bu durumda, başlamadan önce üzerinde ne kadar çalışmak istediğinizi bize bildirmek zorunda olursunuz.

- **İçerik güncelleştirmeleri**. Belge kümesinin her ne kadar kolay olduğu, içerik daha kolay geçmiş hale gelir ve düzeltme gerektirir. Bunlara ek olarak, çeşitli nedenlerle bazı içerikler yinelenmiş veya hatta Üçlü hale geliştirilmiştir. İçeriği güncelleştirmek, tek tek konuların geçerli olduğundan emin olmanızı veya bir özellik alanındaki içeriğin yeniden güncelleştirilmesini sağlayarak yinelemeyi ortadan kaldırmak ve tüm benzersiz içeriklerin daha küçük belge kümesinde korunduğundan emin olmanızı içerir.

- **Yeni içerik yazma**. Kendi konu başlığını yazmak istiyorsanız, bu sorunlar belge ayarımızı eklemek istediğimizi öğrendiğimiz konuları listeler. Bir konu üzerinde çalışmaya başlamadan önce bize bakalım, ancak. Burada listelenmeyen bir konu yazmakla ilgileniyorsanız bir sorun açın.

Ayrıca, ilginizi çekdikleriniz üzerinde çalışmak için [Açık sorunlar](https://github.com/dotnet/docs/issues) listemize ve Volunteer göz atabilirsiniz. Katkı için açık olan sorunları [etiketleyerek, for-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) etiketini kullanırız. 

**2. Adım:** `dotnet/docs`, `dotnet/samples` veya `dotnet/dotnet-api-docs` depoları çatalla ve yaptığınız değişiklikler için bir dal oluşturun.

Küçük değişiklikler için GitHub 'ın Web arabirimini kullanabilirsiniz. Değiştirmek istediğiniz dosyada **Bu projenin çatalınızda dosyayı Düzenle** ' ye tıklamanız yeterlidir. Değişiklikleri gönderdiğinizde GitHub yeni dalı sizin için oluşturur.

**Adım 3:** Bu yeni dalda değişiklikleri yapın.

Yeni bir konu ise, bu [şablon dosyasını](./styleguide/template.md) başlangıç noktası olarak kullanabilirsiniz. Yazma kılavuzunu içerir ve aynı zamanda yazar bilgileri gibi her bir makale için gereken meta verileri açıklar.

Adım 1 ' deki makalenize göre belirlenen TOC konumuna karşılık gelen klasöre gidin.
Bu klasör, bu bölümdeki tüm makalelerin markın dosyalarını içerir.
Gerekirse, içeriğinizin dosyalarını yerleştirmek için yeni bir klasör oluşturun. Bu bölümün ana makalesi *index.MD*olarak adlandırılır.
Görüntüler ve diğer statik kaynaklar için, zaten mevcut değilse, makalenizi içeren klasörün içinde *medya* adlı bir alt klasör oluşturun. *Medya* klasörü içinde, makale adına sahip bir alt klasör oluşturun (Dizin dosyası hariç).
Depo kökünün altındaki *örnekler* klasörüne daha büyük örnekler ekleyin.

Doğru markın söz dizimini izlediğinizden emin olun. Daha fazla bilgi için bkz. [Stil Kılavuzu](./styleguide/template.md).

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

**4. Adım:** Dalınızdan bir çekme Isteği (PR) `dotnet/docs/master`, `dotnet/dotnet-api-docs/master` veya `dotnet/samples/master` ' e gönderir.

PR 'niz *her zaman* deponun varsayılan dalını hedeflemelidir (bir yayın dalı üzerinde çalışmadığınız müddetçe). DotNet/docs için ana dal varsayılan daldır. Yerelleştirilmiş depolar için, dinamik dal varsayılan bir. DotNet/docs üzerinde canlı dalı hedefleyen bir PR 'yi *asla* açmanız gerekir.

Her bir çekme isteği genellikle tek seferde bir sorunu ele almalıdır. PR bir veya daha fazla dosyayı değiştirebilir. Farklı dosyalarda birden çok düzeltmeyi adreslendirirken ayrı PR 'ler tercih edilir.

Çekme isteği mevcut bir sorunu ele alıyorsa, işleme iletisine veya PR açıklamasına `Fixes #Issue_Number` anahtar sözcüğünü ekleyin. Bu şekilde, çekme isteği birleştirildiğinde sorun otomatik olarak kapatılır. Daha fazla bilgi için bkz. [kayıt iletileri aracılığıyla sorunları kapatma](https://help.github.com/articles/closing-issues-via-commit-messages/).

.NET ekibi, çekme kodunuzu inceleyerek, onaylamak için gereken diğer güncelleştirmeler/değişiklikler olup olmadığını size bilmenizi sağlar.

**5. Adım:** Takımda tüm gerekli güncelleştirmeleri ekiple anlatıldığı şekilde yapın.

Bakım, geri bildirim uygulandıktan sonra değişiklik onaylandıktan sonra ana dalda çekme işlemini birleştirir.

Belirli bir temposunda, Ana daldaki tüm işlemeleri canlı dala ityoruz ve sonra katkınızı https://docs.microsoft.com/dotnet/ ' da canlı olarak görebileceksiniz.

### <a name="contributing-to-samples"></a>Örneklere katkıda bulunma

Depomızda bulunan kod için aşağıdaki ayrım yaptık:

- Örnekler: okuyucular örnekleri indirebilir ve çalıştırabilir. Tüm örnekler, tamamlanmış uygulamalar veya kitaplıklar olmalıdır. Örneğin, örnek bir kitaplık oluşturduğunda, birim testlerini veya okuyucuların kodu çalıştırmasına izin veren bir uygulamayı içermesi gerekir.

- Kod parçacıkları: daha küçük bir kavram veya görev gösterir. Bunlar derlemelerdir, ancak bunların tamamen uygulamalar olması amaçlanmamıştır.

Kod hepsi [DotNet/Samples](https://github.com/dotnet/samples) deposunda bulunur. Örnek klasör yapımızın belge klasörü yapısıyla eşleştiği bir modele doğru çalışıyoruz. İzlediğimiz standartlar şunlardır:

- En üst düzey *parçacıklar* klasörü, küçük, odaklanmış örnekler için kod parçacıkları içerir.
- API başvuru örnekleri şu düzenin ardından bir klasörde yer alan: *parçacıklar/\<language >/api/\<namespace >/\<apiname >* .
- Diğer üst düzey klasörler, *docs* deposundaki en üst düzey klasörlerle eşleşir. Örneğin, docs deposunda *makine öğrenimi/öğreticiler* klasörü ve Machine Learning öğreticilerinin örnekleri, *Samples/Machine-Learning/öğreticiler* klasöründedir.

Ayrıca, *çekirdek* ve *Standart* klasörler altındaki tüm örneklerin .NET Core tarafından desteklenen tüm platformlarda oluşturulması ve çalışması gerekir. CI derleme sistemimiz bunu zorunlu kılacak. En üst düzey *çerçeve* klasörü yalnızca Windows 'da oluşturulan ve doğrulanan örnekleri içerir.

Docs deposu yeni içerik eklediği için bu dizinleri genişletebiliriz. Örneğin, `xamarin-ios` ve `xamarin-android` dizinleri gibi Xamarin dizinleri ekleyeceğiz.

Oluşturduğunuz her bir bütün örnek bir *README.MD* dosyası içermelidir. Bu dosya, örneğin kısa bir açıklamasını (bir veya iki paragraf) içermelidir. *README.MD* , okuyuculara bu örneği inceleyerek öğrendikleri şeyleri anlatmalıdır. *README.MD* dosyası ayrıca [.net belgeleri sitesindeki](https://docs.microsoft.com/dotnet/welcome)canlı belgenin bir bağlantısını içermelidir.
Depodaki belirli bir dosyanın bu siteyle eşlendiği yeri öğrenmek için, depo yolundaki `/docs` ' ı `https://docs.microsoft.com/dotnet` ile değiştirin.

Konağınız Ayrıca örneğe bağlantılar da içerir. GitHub 'daki örnek klasörünü doğrudan bağlayın.

Daha fazla bilgi için bkz. [Samples Readme](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>C# Etkileşimli deneyim

İçindeki C# kısa kod örnekleri, tarayıcıda çalışan bir C# örnek belirtmek için `csharp-interactive` dil etiketini kullanabilir. (Satır içi kod örnekleri `csharp-interactive` etiketini kullanır, kaynaktan içerilen kod parçacıkları için `code-csharp-interactive` etiketini kullanın.) Bu kod örnekleri, makalede bir kod penceresi ve bir çıkış penceresi görüntüler. Çıktı penceresinde, Kullanıcı örneği çalıştırdıktan sonra etkileşimli kodu yürütmenin tüm çıktıları görüntülenir. 

Etkileşimli C# deneyim, örneklerle nasıl çalışadığımızda değişiklik yaptığı şekilde değişir. Ziyaretçiler, sonuçları görmek için örneği çalıştırabilir. Örnek veya ilgili metnin çıkış hakkındaki bilgileri içermesi gerekip gerekmediğini belirlemenize yardımcı olan bir dizi etken.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Örnek çalıştırmadan beklenen çıkışın ne zaman görüntüleneceği

- Yeni başlayanlar için tasarlanan makaleler, okuyucuların, işinin çıkışını beklenen Yanıtla karşılaştırabilmesi için çıkış sağlamalıdır.
- Çıktının konuya tamsayı olduğu örnekler bu çıktıyı görüntülemelidir. Örneğin, biçimlendirilen metin makaleleri örneği çalıştırmadan metin biçimini göstermelidir.
- Hem örnek hem de beklenen çıkış kısaysa, çıktıyı göstermeyi göz önünde bulundurun. Biraz zaman kazandırır.
- Geçerli kültürün veya sabit kültürün çıktıyı nasıl etkileyeceğini açıklayan makaleler beklenen çıktıyı açıklamalıdır. Linux tabanlı bir konakta etkileşimli REPL (okuma, yazdırma döngüsünü değerlendir) çalışır. Varsayılan kültür ve sabit kültür farklı işletim sistemlerinde ve makinelerde farklı çıktılar üretir. Makale, Windows, Linux ve Mac sistemlerindeki çıktıyı açıklamalıdır.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Beklenen çıktının örnekten ne zaman dışlanacağını 

- Örneğin, örneğin daha büyük bir çıktı oluşturduğu makaleler açıklamalarda bunu içermemelidir. Örnek çalıştırıldıktan sonra kodu gizler.
- Örneğin bir konuyu gösteren makaleler, ancak bunu anlamak için tam sayı değildir. Örneğin, sorgu sözdizimini açıklamak ve sonra çıktı koleksiyonundaki her öğeyi göstermek için bir LINQ sorgusu çalıştıran kod.

## <a name="contributor-license-agreement"></a>Katkıda bulunan lisans sözleşmesi

Çekme isteği birleştirilmeden önce [.net Foundation katkı lisans sözleşmesi 'ni (CLA)](https://cla.dotnetfoundation.org) imzalamanız gerekir. Bu, .NET Foundation 'daki projeler için tek seferlik bir gereksinimdir. [Vivon 'Da katkı lisans sözleşmeleri (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) hakkında daha fazla bilgi edinebilirsiniz.

Sözleşme: [net-Foundation-Contribution-License-Agreement. PDF](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Anlaşmanın ön ucuna kaydolmanız gerekmez. PR 'yi her zamanki gibi kopyalayabilir, çatalla ve gönderebilirsiniz. Çekme isteği oluşturulduğunda, bir CLA bot tarafından sınıflandırıldı. Değişiklik önemsiz ise (örneğin, bir typo 'yi düzelttik), PR `cla-not-required` ile etiketlenir. Aksi takdirde, `cla-required` olarak sınıflandırılır. CLA 'yı imzaladıktan sonra, geçerli ve gelecekteki tüm çekme istekleri `cla-signed` olarak etiketlenir.
