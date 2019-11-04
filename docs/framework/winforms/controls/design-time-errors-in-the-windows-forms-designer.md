---
title: Windows Form Tasarımcısı tasarım zamanı hataları
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0dd112f89071f6981b438a79f350dfab02af73d5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460111"
---
# <a name="windows-forms-designer-error-page"></a>Windows Form Tasarımcısı hata sayfası

Kodunuzda, üçüncü taraf bir bileşende veya başka bir yerde bir hata nedeniyle Windows Form Tasarımcısı yüklenemezse, tasarımcı yerine bir hata sayfası görürsünüz. Bu hata sayfası Tasarımcıda bir hatayı işaret etmeyebilir. Hata,-form adı > \<adlı arka plan kod sayfasında bir yerde olabilir. Designer.cs. Hatalar, kod sayfasındaki hatanın konumuna atlayabileceğiniz bir bağlantı içeren daraltılabilir, sarı çubuklarda görünür.

![Windows Form Tasarımcısı hata sayfası](media/windows-forms-designer-error-page-collapsed.png)

Hataları yoksayıp, **Yoksay ve devam et '** i tıklatarak tasarımcıyı yüklemeye devam etmeyi seçebilirsiniz. Bu eylem beklenmeyen davranışlara neden olabilir, örneğin, denetimler tasarım yüzeyinde görünmeyebilir.

## <a name="instances-of-this-error"></a>Bu hatanın örnekleri

Sarı hata çubuğu genişletildiğinde, hatanın her örneği listelenir. Birçok hata türü, aşağıdaki biçimde tam bir konum içerir: *[proje adı]* *[Form adı]* satır: *[satır numarası]* sütun: *[sütun numarası]* . Bir çağrı yığını hatayla ilişkilendirilmişse, bunu görmek için **çağrı yığınını göster** bağlantısına tıklayabilirsiniz. Çağrı yığınını incelemek, hatayı çözmenize yardımcı olabilir.

![Windows Form Tasarımcısı genişletilmiş hata](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - Visual Basic uygulamalar için tasarım zamanı hata sayfasında birden fazla hata görüntülenmez, ancak aynı hatanın birden fazla örneğini görüntüleyebilir.
> - Uygulamalar C++ için hataların kod konumu bağlantıları yoktur.

## <a name="help-with-this-error"></a>Bu hatayla ilgili yardım

Hata için bir yardım konusu varsa, docs.microsoft.com adresindeki yardım sayfasına doğrudan gitmek için **MSDN yardım** bağlantısına tıklayın.

## <a name="forum-posts-about-this-error"></a>Bu hatayla ilgili forum gönderileri

Microsoft Developer Network forumları ' na gitmek için **Bu hata bağlantısıyla ilgili olarak MSDN forumlarını arayın** . [Windows Form Tasarımcısı](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) veya [Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) forumlarında özel olarak arama yapmak isteyebilirsiniz.

## <a name="design-time-errors"></a>Tasarım zamanı hataları

Bu bölümde karşılaşabileceğiniz hatalardan bazıları listelenir.

### <a name="identifier-name-is-not-a-valid-identifier"></a>'\<tanımlayıcı adı > ' geçerli bir tanımlayıcı değil

Bu hata, bir alanın, yöntemin, etkinliğin veya nesnenin yanlış adlandırıldığını gösterir.

### <a name="name-already-exists-in-project-name"></a>'\<name > ' '\<proje adı > ' içinde zaten var

Hata iletisi: "'\<name > ' '\<proje adı > ' içinde zaten var. Lütfen benzersiz bir ad girin. "

Projede zaten var olan devralınmış bir form için bir ad belirttiniz. Bu hatayı düzeltmek için devralınan forma benzersiz bir ad verin.

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>'\<araç kutusu sekme adı > ' bir araç kutusu kategorisi değil

Bir üçüncü taraf tasarımcı, araç kutusundaki mevcut olmayan bir sekmeye erişmeye çalıştı. Bileşen satıcısına başvurun.

### <a name="a-requested-language-parser-is-not-installed"></a>İstenen bir dil ayrıştırıcı yüklü değil

Hata iletisi: "istenen dil ayrıştırıcısı yüklü değil. Dil ayrıştırıcı adı '{0}'. "

Visual Studio, dosya türü için kaydedilen ancak desteklenmeyen bir tasarımcı yüklemeye çalıştı. Bu, büyük olasılıkla kurulum sırasında oluşan bir hata nedeniyle oluşur. Bir çözüm için kullanmakta olduğunuz dilin satıcısına başvurun.

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>Kaynak kodunu üretmek ve ayrıştırmak için gerekli olan hizmet eksik

Bu bir üçüncü taraf bileşeniyle ilgili bir sorundur. Bileşen satıcısına başvurun.

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>'\<nesne adı > ' örneği oluşturulmaya çalışılırken özel durum oluştu

Hata iletisi: "'\<nesne adı > ' örneği oluşturulmaya çalışılırken özel durum oluştu. Özel durum "\<özel durum dizesi\>" idi.

Üçüncü taraf tasarımcı, Visual Studio 'Nun bir nesne oluşturmasını istedi, ancak nesne bir hata oluşturdu. Bileşen satıcısına başvurun.

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>Başka bir düzenleyicide '\<belge adı > ' uyumsuz modda açık

Hata iletisi: "başka bir düzenleyicide '\<belge adı > ' uyumsuz modda açılmış. Lütfen düzenleyiciyi kapatın ve bu işlemi yeniden deneyin. "

Bu hata, zaten başka bir düzenleyicide açılmış olan bir dosyayı açmaya çalıştığınızda ortaya çıkar. Zaten açık dosyayı olan düzenleyici gösteriliyor. Bu hatayı düzeltmek için, dosyayı açık olan düzenleyiciyi kapatın ve yeniden deneyin.

### <a name="another-editor-has-made-changes-to-document-name"></a>Başka bir düzenleyici '\<belge adı > ' üzerinde değişiklikler yaptı

Değişikliklerin etkili olması için tasarımcıyı kapatıp yeniden açın. Normal olarak, değişiklikler yapıldıktan sonra Visual Studio otomatik olarak tasarımcı 'yı yeniden yükler. Ancak, üçüncü taraf bileşen tasarımcıları gibi diğer tasarımcılar yeniden yükleme davranışını desteklemiyor olabilir. Bu durumda, Visual Studio, tasarımcıyı el ile kapatıp yeniden açmanızı ister.

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>Dosya başka bir düzenleyicide uyumsuz modda açılmış

Hata iletisi: "başka bir düzenleyici dosyanın uyumsuz modda açık olduğunu. Lütfen düzenleyiciyi kapatın ve bu işlemi yeniden deneyin. "

Bu ileti "başka bir düzenleyicide '\<belge adı > ' uyumsuz bir modda açık" olduğundan, ancak Visual Studio dosya adını saptayamıyor. Bu hatayı düzeltmek için, dosyayı açık olan düzenleyiciyi kapatın ve yeniden deneyin.

### <a name="array-rank-rank-in-array-is-too-high"></a>Dizi > ' dizisinde dizi derecelendirmesi '\<sıralaması çok yüksek

Visual Studio yalnızca tasarımcı tarafından ayrıştırılmış kod bloğundaki tek boyutlu dizileri destekler. Çok boyutlu diziler bu alanın dışında geçerli.

### <a name="assembly-assembly-name-could-not-be-opened"></a>'\<bütünleştirilmiş kod adı > ' derlemesi açılamadı

Hata iletisi: "derleme '\<derleme adı > ' açılamadı. Dosyanın hala mevcut olduğunu doğrulayın. "

Bu hata iletisi, açılmayan bir dosyayı açmaya çalıştığınızda ortaya çıkar. Dosyanın var olduğunu ve geçerli bir derleme olduğunu doğrulayın.

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>Hatalı öğe türü. Bu serileştirici, '\<tür adı > ' türünde bir öğe bekliyor

Bu bir üçüncü taraf bileşeniyle ilgili bir sorundur. Bileşen satıcısına başvurun.

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>Şu anda Visual Studio Araç Kutusuna erişilemiyor

Visual Studio, araç kutusu için kullanılabilir olmayan bir çağrı yaptı. Bu hatayı görürseniz, bu hatayı görürseniz lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>'\<olay adı > ' olayına bir olay işleyicisi bağlanamaz çünkü salt okunurdur

Bu hata, genellikle bir olayı temel sınıftan devralınan bir denetime bağlamayı denediğinizde ortaya çıkar. Denetimin üye değişkeni Private ise, Visual Studio olayı yöntemine bağlanamaz. Özel olarak devralınan denetimlere ek olaylar bağlanamaz.

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>İstenen bileşen tasarım kapsayıcısının üyesi olmadığından bileşen için bir yöntem adı oluşturulamıyor

Visual Studio, tasarımcıda üye değişkeni olmayan bir bileşene olay işleyicisi eklemeye çalıştı. Bileşen satıcısına başvurun.

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>'\<name > ' nesnesi zaten '\<name > ' olarak adlandırıldığından adlandırılamıyor

Bu, Visual Studio seri hale getiricide bir iç hatadır. Seri hale getiricinin, desteklenmeyen bir nesneyi iki kez yeniden adlandırma girişiminde bulunduğunu belirtir. Bu hatayla karşılaşırsanız lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>Devralınan '\<bileşen adı > ' bileşeni kaldırılamaz veya yok edilemez

Devralınan denetimler, devralan sınıfının sahipliğinin altındadır. Devralınan denetimdeki değişiklikler denetimin kaynaklandığı sınıfta yapılmalıdır. Bu nedenle, yeniden adlandıramaz veya yok edilemez.

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>'\<araç kutusu sekme adı > ' kategorisinin '\<class name > ' sınıfı için bir aracı yok

Tasarımcı, belirli bir araç kutusu sekmesindeki bir sınıfa başvurmaya çalıştı, ancak sınıf yok. Bileşen satıcısına başvurun.

### <a name="class-class-name-has-no-matching-constructor"></a>'\<class name > ' sınıfının eşleşen bir oluşturucusu yok

Üçüncü taraf tasarımcı, Visual Studio 'Nun mevcut olmayan oluşturucuda belirli parametrelere sahip bir nesne oluşturmasını istedi. Bileşen satıcısına başvurun.

### <a name="code-generation-for-property-property-name-failed"></a>'\<Özellik adı > ' özelliği için kod üretimi başarısız oldu

Bu bir hata için genel bir sarmalayıcıdır. Bu iletiye eşlik eden hata dizesi, hata iletisi hakkında daha fazla ayrıntı verir ve daha belirli bir Yardım konusunun bağlantısına sahip olur. Bu hatayı düzeltmek için, bu hataya eklenen hata iletisinde belirtilen hatayı ele edin.

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>'\<bileşen adı > ' bileşeni, kurucusunda Container. Add () çağrısını gerçekleştirmedi

Bu, yeni yüklediğiniz veya forma yerleştirdiğiniz bileşendeki bir hatadır. Bileşenin kendisini kapsayıcı denetimine eklemediğini belirtir (bunun başka bir denetim veya form olup olmadığı). Tasarımcı çalışmaya devam eder, ancak çalışma zamanında bileşenle ilgili sorunlar olabilir.

Hatayı düzeltmek için bileşen satıcısına başvurun. Ya da, oluşturduğunuz bir bileşen ise bileşenin oluşturucusunda `IContainer.Add` yöntemini çağırın.

### <a name="component-name-cannot-be-empty"></a>Bileşen adı boş olamaz

Bu hata, bir bileşeni boş bir değere yeniden adlandırmaya çalıştığınızda ortaya çıkar.

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>Henüz başlatılamadığından '\<değişken adı > ' değişkenine erişilemedi

Bu hata, iki senaryo nedeniyle ortaya çıkabilir. Üçüncü taraf bir bileşen satıcısı, dağıttıkları bir denetim veya bileşenle ilgili bir sorun içeriyor veya yazdığınız kod bileşenler arasında özyinelemeli bağımlılıklara sahip.

Bu hatayı düzeltmek için, kodunuzun özyinelemeli bir bağımlılığı olmadığından emin olun. Bu tür sorunlardan biri ücretsizdir, hata iletisinin tam metnini aklınızda yazın ve bileşen satıcısına başvurun.

### <a name="could-not-find-type-type-name"></a>'\<tür adı > ' türü bulunamadı

Hata iletisi: "'\<tür adı > ' türü bulunamadı. Lütfen bu türü içeren derlemeye başvurulduğundan emin olun. Bu tür geliştirme projenizin bir parçasıysa, projenin başarılı bir şekilde oluşturulduğundan emin olun. "

Bir başvuru bulunamadığı için bu hata oluştu. Hata iletisinde belirtilen türün başvurulduğundan ve türün gerektirdiği tüm derlemelere de başvurulduğundan emin olun. Genellikle, sorun çözümdeki bir denetimin oluşturulmamasından kaynaklanır. Derlemek için **derleme** menüsünden **çözüm oluştur** ' u seçin. Aksi takdirde, denetim zaten oluşturulsa, Çözüm Gezgini **Başvurular** veya **Bağımlılıklar** klasörünün sağ tıklama menüsünden el ile bir başvuru ekleyin.

### <a name="could-not-load-type-type-name"></a>'\<tür adı > ' türü yüklenemedi

Hata iletisi: "'\<tür adı > ' türü yüklenemedi. Lütfen bu türü içeren derlemenin proje başvurularına eklendiğinden emin olun. "

Visual Studio bir olay işleme yöntemi oluşturmaya çalıştı ve yöntem için bir veya daha fazla parametre türü bulamadı. Bunun nedeni genellikle eksik bir başvurudur. Bu hatayı düzeltmek için, türü içeren başvuruyu projeye ekleyin ve yeniden deneyin.

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>Devralınan bileşenler için proje öğesi şablonlarının konumu bulunamadı

Visual Studio 'da devralınan formlara yönelik şablonlar kullanılamıyor. Bu hatayla karşılaşırsanız lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>'\<class name > ' temsilci sınıfında Invoke yöntemi yok. Bu sınıf bir temsilci mi?

Visual Studio bir olay işleyicisi oluşturmaya çalıştı, ancak olay türünde bir sorun oluştu. Olay CLS uyumlu olmayan bir dil tarafından oluşturulduysa bu durum oluşabilir. Bileşen satıcısına başvurun.

### <a name="duplicate-declaration-of-member-member-name"></a>'\<üye adı > ' üyesinin yinelenen bildirimi

Bir üye değişkeni iki kez bildirildiği için bu hata oluşur (örneğin, `Button1` adında iki denetim kodda bildirildiği için). Adların devralınan formlarda benzersiz olması gerekir. Ayrıca, adlar yalnızca büyük/küçük harf bakımından farklı olamaz.

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>'\<kültür adı > ' kültürü için kaynak dosyasındaki kaynakları okuma hatası

Bu hata, projede hatalı bir. resx dosyası varsa oluşabilir.

Bu hatayı düzeltmek için:

1. Çözümle ilişkili. resx dosyalarını görüntülemek için Çözüm Gezgini içindeki **tüm dosyaları göster** düğmesine tıklayın.
2. . Resx dosyasını XML düzenleyicisinde,. resx dosyasına sağ tıklayıp **Aç**' ı seçerek yükleyin.
3. Hataları gidermek için. resx dosyasını el ile düzenleyin.

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>'\<kültür adı > ' varsayılan kültürünün kaynak dosyasındaki kaynakları okuma hatası

Bu hata, varsayılan kültür için projede bir hatalı. resx dosyası varsa meydana gelir.

Bu hatayı düzeltmek için:

1. Çözümle ilişkili. resx dosyalarını görüntülemek için Çözüm Gezgini içindeki **tüm dosyaları göster** düğmesine tıklayın.
2. . Resx dosyasını XML düzenleyicisinde,. resx dosyasına sağ tıklayıp **Aç**' ı seçerek yükleyin.
3. Hataları gidermek için. resx dosyasını el ile düzenleyin.

### <a name="failed-to-parse-method-method-name"></a>'\<Yöntem adı > ' metodu ayrıştırılamadı

Hata iletisi: "Yöntem adı > '\<metodu ayrıştırılamadı. Ayrıştırıcı şu hatayı bildirdi: '\<hata dizesi > '. Olası hatalar için lütfen Görev Listesi bakın. "

Bu, ayrıştırma sırasında ortaya çıkan sorunlar için genel bir hata iletisidir. Bu hatalar genellikle söz dizimi hataları nedeniyle yapılır. Hatayla ilgili belirli iletiler için Görev Listesi bakın.

### <a name="invalid-component-name-component-name"></a>Geçersiz bileşen adı: '\<bileşen adı > '

Bir bileşeni bu dil için geçersiz bir değerle yeniden adlandırmaya çalıştınız. Bu hatayı düzeltmek için, bileşeni bu dilin adlandırma kurallarıyla uyumlu olacak şekilde adlandırın.

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>'\<class name > ' türü aynı dosyadaki birkaç kısmi sınıftan yapılır

[Kısmi](../../../csharp/language-reference/keywords/partial-type.md) anahtar sözcüğünü kullanarak birden çok dosyada bir sınıf tanımladığınızda, her dosyada yalnızca bir kısmi tanımınız olabilir.

Bu hatayı düzeltmek için, sınıfınızın kısmi tanımlarından birini, dosyadan kaldırın.

### <a name="the-assembly-assembly-name-could-not-be-found"></a>'\<bütünleştirilmiş kod adı > ' derlemesi bulunamadı

Hata iletisi: "\<bütünleştirilmiş kod adı > ' bulunamadı. Derlemeye başvurulduğundan emin olun. Derleme, geçerli geliştirme projesinin bir parçasıysa, projenin oluşturulduğundan emin olun. "

Bu hata, "'\<tür adı > ' bulunamadı" olarak benzerdir, ancak bu hata genellikle meta veri özniteliği nedeniyle oluşur. Bu hatayı düzeltmek için, öznitelikler tarafından kullanılan tüm derlemelerin başvurulduğundan emin olun.

### <a name="the-assembly-name-assembly-name-is-invalid"></a>'\<bütünleştirilmiş kod adı > ' derleme adı geçersiz

Bir bileşen belirli bir derlemeyi istedi, ancak bileşen tarafından girilen ad geçerli bir derleme adı değil. Bileşen satıcısına başvurun.

### <a name="the-base-class-class-name-cannot-be-designed"></a>'\<class name > ' temel sınıfı tasarlanamıyor

Visual Studio sınıfını yükledi, ancak sınıfın uygulayıcısı bir tasarımcı sağlamadığı için sınıf tasarlanamıyor. Sınıf bir tasarımcıyı destekliyorsa, derleyici hataları gibi bir tasarımcıda görüntülemede sorun oluşmasına neden olabilecek bir sorun olmadığından emin olun. Ayrıca, sınıfa yapılan tüm başvuruların doğru olduğundan ve tüm sınıf adlarının doğru yazıldığından emin olun. Aksi takdirde, sınıf bir gösterimde değilse kod görünümünde düzenleyin.

### <a name="the-base-class-class-name-could-not-be-loaded"></a>'\<class name > ' temel sınıfı yüklenemedi

Sınıfın projede başvurulmadığından, Visual Studio tarafından yüklenemez. Bu hatayı düzeltmek için, projedeki sınıfa bir başvuru ekleyin ve Windows Form Tasarımcısı penceresini kapatıp yeniden açın.

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>'\<class name > ' sınıfı, Visual Studio 'nun bu sürümünde tasarlanabilir

Bu denetim veya bileşen için tasarımcı, Visual Studio 'Nun desteklediği türleri desteklemez. Bileşen satıcısına başvurun.

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>Sınıf adı bu dil için geçerli bir tanımlayıcı değil

Kullanıcı tarafından oluşturulan kaynak kodun, kullanılmakta olan dil için geçerli olmayan bir sınıf adı vardır. Bu hatayı düzeltmek için, sınıfı dil gereksinimlerine uygun olacak şekilde adlandırın.

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>Bileşen, '\<başvuru adı > ' öğesine döngüsel bir başvuru içerdiğinden eklenemiyor

Kendisini bir denetim veya bileşen ekleyemezsiniz. Bunun gerçekleşebileceği başka bir durum da, bir formun InitializeComponent yönteminde (örneğin, Form1) bir Form1'in başka bir örneğini oluşturan bir kod varsa.

### <a name="the-designer-cannot-be-modified-at-this-time"></a>Tasarımcı şu anda değiştirilemez

Bu hata, düzenleyicideki dosya salt okunurdur olarak işaretlendiğinde oluşur. Dosyanın salt okunurdur ve uygulamanın çalışmadığını doğrulayın.

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>Bu dosyanın içindeki sınıflardan hiçbiri tasarlanamadığından dosya için tasarımcı görüntülenemedi

Visual Studio, tasarımcı gereksinimlerini karşılayan bir temel sınıf bulamadığında bu hata oluşur. Formlar ve denetimler, tasarımcıları destekleyen bir taban sınıftan türetilmelidir. Devralınan bir formdan veya denetimden türetmeniz durumunda, projenin oluşturulduğundan emin olun.

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>'\<class name > ' temel sınıfı için tasarımcı yüklü değil

Visual Studio, sınıf için tasarımcıyı yükleyemedi. Bu hatayla karşılaşırsanız lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>Tasarımcı '\<tür adı > ' türünde bir örnek oluşturmalı, ancak tür abstract olarak bildirildiği için bu işlemi yapamıyor

Bu hata oluştuğundan, tasarımcıya geçirilen nesnenin temel sınıfı [soyut](../../../csharp/language-reference/keywords/abstract.md)olduğundan, buna izin verilmez.

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>Dosya tasarımcıya yüklenemedi

Bu dosyanın temel sınıfı hiçbir tasarımcıları desteklemez. Geçici bir çözüm olarak, dosya üzerinde çalışmak için kod görünümünü kullanın. Çözüm Gezgini dosyaya sağ tıklayın ve **kodu görüntüle**' yi seçin.

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>Bu dosyanın dili, gerekli kod ayrıştırma ve üretme hizmetlerini desteklemiyor

Hata iletisi: "Bu dosyanın dili, gerekli kod ayrıştırma ve oluşturma hizmetlerini desteklemiyor. Lütfen açtığınız dosyanın bir projenin üyesi olduğundan emin olun ve sonra dosyayı açmayı yeniden deneyin. "

Bu hata, büyük olasılıkla, tasarımcıları desteklemeyen bir projede bulunan bir dosyayı açmaktan kaynaklanıyor.

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>'\<class name > ' dil ayrıştırıcı sınıfı düzgün şekilde uygulanmadı

Hata iletisi: "\<class name > ' dil ayrıştırıcı sınıfı düzgün şekilde uygulanmadı. Güncelleştirilmiş bir Ayrıştırıcı modülü için satıcıya başvurun. "

Kullanımdaki dil, doğru temel sınıftan türemeyen bir tasarımcı sınıfına kaydoldu. Kullanmakta olduğunuz dilin satıcısıyla iletişim kurun.

### <a name="the-name-name-is-already-used-by-another-object"></a>'\<name > ' adı zaten başka bir nesne tarafından kullanılıyor

Bu, Visual Studio seri hale getiricide bir iç hatadır. Bu hatayla karşılaşırsanız lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>'\<nesne adı > ' nesnesi IComponent arabirimini uygulamıyor

Visual Studio bir bileşen oluşturmaya çalıştı, ancak oluşturulan nesne <xref:System.ComponentModel.IComponent> arabirimini uygulamıyor. Bir çözüm için bileşen satıcısına başvurun.

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>'\<nesne adı > ' nesnesi '\<Özellik adı > ' özelliği için null döndürdü, ancak buna izin verilmiyor

Her zaman bir nesne döndürmesi gereken bazı .NET özellikleri vardır. Örneğin, bir formun **denetimler** koleksiyonu, içinde hiç denetim olmadığı halde her zaman bir nesne döndürmelidir.

Bu hatayı düzeltmek için, hatada belirtilen özelliğin null olmadığından emin olun.

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>Seri hale getirme veri nesnesi doğru türde değil

Seri hale getirici tarafından sunulan bir veri nesnesi, kullanılmakta olan geçerli seri hale getirici ile eşleşen bir türün örneği değildir. Bileşen satıcısına başvurun.

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>'\<hizmet adı > ' hizmeti gerekli, ancak bulunamadı

Hata iletisi: "hizmet '\<hizmet adı > ' gereklidir, ancak bulunamadı. Visual Studio yüklemenizde bir sorun olabilir. "

Visual Studio için gereken bir hizmet kullanılamıyor. Bu tasarımcıyı desteklemeyen bir projeyi yüklemeye çalışıyorsanız, ihtiyacınız olan değişiklikleri yapmak için kod düzenleyicisini kullanın. Aksi takdirde, bu hatayı görürseniz lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>Hizmet örneği '\<arabirim adı > ' öğesinden türetilmeli veya bunu uygulamalıdır

Bu hata, bir bileşen veya bileşen tasarımcısının bir arabirim ve nesne gerektiren **AddService** yöntemini çağırdığını, ancak belirtilen nesnenin belirtilen arabirimi uygulamıyor olduğunu gösterir. Bileşen satıcısına başvurun.

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>Kod penceresindeki metin değiştirilemedi

Hata iletisi: "kod penceresindeki metin değiştirilemedi. Dosyanın salt okunurdur ve yeterli disk alanı olup olmadığını denetleyin. "

Bu hata, Visual Studio disk alanı veya bellek sorunları nedeniyle bir dosyayı düzenleyemediğinde veya dosya salt okunurdur olarak işaretlendiğinden oluşur.

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>Araç Kutusu numaralandırıcı nesnesi bir seferde sadece tek bir öğe almayı destekler

Bu hatayı görürseniz, bu hatayı görürseniz lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>'\<bileşen adı > ' araç kutusu öğesi araç kutusundan alınamadı

Hata iletisi: "'\<bileşen adı > ' araç kutusu öğesi araç kutusundan alınamadı. Araç kutusu öğesini içeren derlemenin düzgün yüklendiğinden emin olun. Araç kutusu öğesi şu hatayı verdi: \<hata dizesi >. "

Söz konusu bileşen, Visual Studio 'Ya eriştiğinde bir özel durum oluşturdu. Bileşen satıcısına başvurun.

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>'\<araç kutusu öğe adı > ' için araç kutusu öğesi araç kutusundan alınamadı

Hata iletisi: "'\<araç kutusu öğe adı > ' araç kutusu öğesi araç kutusundan alınamadı. Öğeyi araç kutusundan kaldırmayı ve geri eklemeyi deneyin. "

Araç kutusu öğesi içindeki veriler bozuksa veya bileşenin sürümü değiştirilmişse bu hata oluşur. Araç kutusundan öğeyi kaldırmayı ve tekrar eklemeyi deneyin.

### <a name="the-type-type-name-could-not-be-found"></a>'\<tür adı > ' türü bulunamadı

Hata iletisi: "\<tür adı > ' türü bulunamadı. Türü içeren derlemeye başvurulduğundan emin olun. Derleme, geçerli geliştirme projesinin bir parçasıysa, projenin oluşturulduğundan emin olun. "

Tasarımcı yüklenirken, Visual Studio bir tür bulamadı. Türü içeren derlemeye başvurulduğundan emin olun. Derleme, geçerli geliştirme projesinin bir parçasıysa, projenin oluşturulduğundan emin olun.

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>Tür çözümleme hizmeti yalnızca ana uygulama iş parçacığından çağrılabilir

Visual Studio, hatalı iş parçacığından gerekli kaynaklara erişmeyi denedi. Bu hata, tasarımcıyı oluşturmak için kullanılan kod, ana uygulama iş parçacığı dışında bir iş parçacığından tür çözümleme hizmeti olarak çağrıldığında görüntülenir. Bu hatayı düzeltmek için, doğru iş parçacığından hizmeti çağırın veya bileşen satıcısına başvurun.

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>'\<değişken adı > ' değişkeni bildirilmemiş ya da hiç atanmadı

Kaynak kodun, başvurmayan veya atanmamış olan **button1**gibi bir değişkene başvurusu vardır. Değişken atanmamıştır, bu ileti hata değil, uyarı olarak görüntülenir.

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>Menü komutu '\<menü komutu için zaten bir komut işleyicisi var > '

Bir üçüncü taraf tasarımcı, komut tablosuna zaten bir işleyicisi olan bir komut eklerse bu hata ortaya çıkar. Bileşen satıcısına başvurun.

### <a name="there-is-already-a-component-named-component-name"></a>'\<bileşen adı > ' adlı bir bileşen zaten var

Hata iletisi: "'\<bileşen adı > ' adlı bir bileşen zaten var. Bileşenler benzersiz adlara sahip olmalıdır ve adların büyük/küçük harfe duyarlı olmaması gerekir. Ayrıca, bir ad devralınmış bir sınıftaki herhangi bir bileşenin adıyla çakışamaz. "

Bu hata iletisi, Özellikler penceresi bileşen adında bir değişiklik olduğunda ortaya çıkar. Bu hatayı düzeltmek için tüm bileşen adlarının benzersiz olduğundan, büyük/küçük harfe duyarlı olmadığından ve devralınan sınıflardaki bileşenlerin adlarıyla çakışmadıklarından emin olun.

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>'\<biçim adı > ' biçiminde kaydedilmiş bir araç kutusu öğe Oluşturucusu zaten var

Bir üçüncü taraf bileşeni bir araç kutusu sekmesindeki bir öğeye geri çağırma yaptı, ancak öğe zaten bir geri çağırma içeriyor. Bileşen satıcısına başvurun.

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>Bu dil altyapısı, bir tasarımcı yüklemek için kullanılacak bir CodeModel modelini desteklemez

Bu ileti "Bu dosyanın dili, gerekli kod ayrıştırma ve oluşturma hizmetlerini desteklemez" olarak benzerdir, ancak bu ileti bir iç kayıt sorunuyla ilgilidir. Bu hatayı görürseniz, bu hatayı görürseniz lütfen [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)' i kullanarak bir sorunu günlüğe kaydedin.

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>'\<tür adı\>' türü, '\<parametre türü adları > ' türünde parametrelere sahip bir oluşturucuya sahip değil

Visual Studio eşleşen parametrelere sahip bir [Oluşturucu](../../../csharp/programming-guide/classes-and-structs/constructors.md) bulamadı. Bu, gerekenden farklı türlere sahip bir Oluşturucu sağlamaya neden olabilir. Örneğin, bir **nokta** Oluşturucusu iki tamsayı alabilir. Kayan noktalar sağladıysanız bu hata oluşur.

Bu hatayı düzeltmek için, farklı bir Oluşturucu kullanın veya parametre türlerini Oluşturucu tarafından sağlananlarla eşleşecek şekilde açıkça atayın.

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>Geçerli uygulamaya '\<başvuru adı > ' başvurusu eklenemiyor

Hata iletisi: "\<başvuru adı > ' başvurusu geçerli uygulamaya eklenemiyor. Farklı bir '\<başvuru adı > ' sürümünün zaten başvurulmadığını denetleyin. "

Visual Studio başvuru ekleyemez. Bu hatayı düzeltmek için, başvurunun farklı bir sürümünün zaten başvurulmadığını denetleyin.

### <a name="unable-to-check-out-the-current-file"></a>Geçerli dosya kullanıma alınamıyor

Hata iletisi: "geçerli dosya denetlenemiyor. Dosya kilitli olabilir veya dosyayı el ile denetlemeniz gerekebilir. "

Bu hata, şu anda kaynak kodu denetimine iade edilmiş bir dosyayı değiştirdiğiniz zaman ortaya çıkar. Genellikle, Visual Studio dosya kullanıma alma iletişim kutusunu gösterir, böylece Kullanıcı dosyayı kullanıma alabilir. Bu kez, kullanıma alma sırasında birleştirme çakışması nedeniyle dosya kullanıma alınmamış olabilir. Bu hatayı düzeltmek için dosyanın kilitli olmadığından emin olun ve ardından dosyayı el ile kullanıma almaya çalışın.

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>'\<Options iletişim kutusu sekme adı > ' adlı sayfa bulunamıyor

Bu hata, bir bileşen Tasarımcısı mevcut olmayan bir ad kullanarak Seçenekler iletişim kutusundan bir sayfaya erişim istediğinde ortaya çıkar. Bileşen satıcısına başvurun.

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>'\<Options iletişim kutusu sekme adı > ' sayfasında '\<Özellik adı > ' özelliği bulunamıyor

Bu hata, bir bileşen Tasarımcısı Seçenekler iletişim kutusundan sayfadaki belirli bir değere erişim istediğinde, ancak bu değer yoksa oluşur. Bileşen satıcısına başvurun.

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>Visual Studio, dosyanın içindeki sınıf görsel olarak tasarlanabilen bir sınıftan devralınmadığından, dosya için bir tasarımcı açamıyor

Visual Studio sınıfı yükledi, ancak bu sınıfa yönelik tasarımcı yüklenemedi. Visual Studio, tasarımcıların bir dosyadaki ilk sınıfı kullanmasını gerektirir. Bu hatayı düzeltmek için sınıf kodunu dosyadaki ilk sınıf olacak şekilde taşıyın ve tasarımcıyı yeniden yükleyin.

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>Visual Studio '\<tür adı > ' türünün örneklerini kaydedemiyor veya yükleyemiyor

Bu bir üçüncü taraf bileşeniyle ilgili bir sorundur. Bileşen satıcısına başvurun.

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>Visual Studio, Tasarım görünümü '\<belge adı > ' açamadı

Hata iletisi: "Visual Studio, Tasarım görünümü '\<belge adı > ' açamadı. Dosya türü için hiçbir ayrıştırıcı yüklenmedi. "

Bu hata, dosya Aç iletişim kutusunda veya Çözüm Gezgini bir dosyayı açmaya çalıştığınızda projenin dilinin bir tasarımcıyı desteklemediğini ve ortaya geçtiğini gösterir. Bunun yerine, dosyayı kod görünümünde düzenleyin.

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>Visual Studio, '\<tür adı > ' türündeki sınıflar için bir tasarımcı bulamadı

Visual Studio sınıfı yükledi, ancak sınıfı tasarlanamıyor. Bunun yerine, sınıfı sağ tıklayıp kodu **görüntüle**' yi seçerek kod görünümündeki sınıfı düzenleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarımcı kullanarak Windows Forms denetimleri geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Windows Form Tasarımcısı Forumu](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
