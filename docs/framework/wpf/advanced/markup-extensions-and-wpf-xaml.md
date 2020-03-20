---
title: Biçimlendirme Uzantıları ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- brace character [WPF]
- Binding markup extensions [WPF]
- RelativeSource markup extensions [WPF]
- XAML [WPF], markup extensions
- markup extensions [WPF]
- nesting extension syntax [WPF]
- curly brace characters ({})
- TemplateBinding markup extensions [WPF]
- StaticResource markup extensions [WPF]
- literal curly brace characters ({})
- characters [WPF], curly brace
- DynamicResource markup extensions [WPF]
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
ms.openlocfilehash: c288055a27cbab75a5cdf541e539ea20e490c965
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141061"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Biçimlendirme Uzantıları ve WPF XAML
Bu konu, sözdizimi kuralları, amacı ve bunların altında yatan sınıf nesnesi modeli de dahil olmak üzere XAML için biçimlendirme uzantıları kavramını tanıtır. Biçimlendirme uzantıları XAML dilinin ve XAML hizmetlerinin .NET uygulamasının genel bir özelliğidir. Bu konu özellikle WPF XAML'de kullanılmak üzere biçimlendirme uzantılarını ayrıntılarıyla anlatır.  

<a name="XAML_Processors_and_Markup_Extensions"></a>
## <a name="xaml-processors-and-markup-extensions"></a>XAML İşlemciler ve Biçimlendirme Uzantıları  
 Genel olarak konuşursak, Bir XAML parlayıcı bir öznitelik değerini ilkel bir dize olarak yorumlayabilir veya bazı yollarla bir nesneye dönüştürebilir. Bu araçlardan biri, bir tür dönüştürücüye başvurmaktır; bu konu [TypeConverters ve XAML](typeconverters-and-xaml.md)belgelenmiştir. Ancak, farklı davranış gerekli senaryolar vardır. Örneğin, bir XAML işlemcisi, bir öznitelik değerinin nesne grafiğinde yeni bir nesneyle sonuçlanmaması gerektiği konusunda talimat verebilir. Bunun yerine, öznitelik, grafiğin başka bir bölümünde zaten oluşturulmuş bir nesneye veya statik nesneye başvuruda bulunan bir nesne grafiğiyle sonuçlanmalıdır. Başka bir senaryo, bir XAML işlemcibir nesnenin oluşturucuiçin varsayılan olmayan bağımsız değişkenler sağlayan bir sözdizimi kullanmak için talimat olabilir. Bunlar, biçimlendirme uzantısının çözümü sağlayabileceği senaryo türleridir.  
  
<a name="Basic_Markup_Extension_Syntax"></a>
## <a name="basic-markup-extension-syntax"></a>Temel Biçimlendirme Uzantısı Sözdizimi  
 Bir öznitelik kullanımındaki özellikler, özellik öğesi kullanımındaki özellikler veya her ikisi için değerler sağlamak için biçimlendirme uzantısı uygulanabilir.  
  
 Bir öznitelik değeri sağlamak için kullanıldığında, biçimlendirme uzantısı dizisini XAML işlemciye ayıran sözdizimi, kıvırcık ayraçların ({ ve }) açılımı ve kapanışının varlığıdır. Biçimlendirme uzantısı türü, açılış kıvırcık ayracından hemen sonra dize belirteci yle tanımlanır.  
  
 Özellik öğesi sözdiziminde kullanıldığında, biçimlendirme uzantısı, özellik öğesi değeri sağlamak için kullanılan diğer tüm elemanlarla görsel olarak aynıdır: biçimlendirme uzantısı sınıfına açı ayraçları (<>) içinde bir öğe olarak başvuran bir XAML öğesi bildirimi.  
  
<a name="XAML_Defined_Markup_Extensions"></a>
## <a name="xaml-defined-markup-extensions"></a>XAML Tanımlı Biçimlendirme Uzantıları  
 XAML'nin WPF uygulamasına özgü olmayan, ancak bunun yerine bir dil olarak XAML'nin içsel uygulamaları veya özellikleri olan birkaç biçimlendirme uzantısı vardır. Bu biçimlendirme uzantıları System.Xaml derlemesinde genel .NET Framework XAML hizmetlerinin bir parçası olarak uygulanır ve XAML dili xaml ad alanı içindedir. Ortak biçimlendirme kullanımı açısından, bu biçimlendirme uzantıları genellikle kullanımdaki `x:` önek tarafından tanımlanabilir. <xref:System.Windows.Markup.MarkupExtension> Temel sınıf (System.Xaml'da da tanımlanan) WPF XAML dahil olmak üzere XAML okuyucularında ve XAML yazarlarında desteklenebilecek şekilde tüm biçimlendirme uzantılarının kullanması gereken deseni sağlar.  
  
- `x:Type`<xref:System.Type> adlı tür için nesne sağlar. Bu tesis en sık stil ve şablonlarda kullanılır. Ayrıntılar için [bkz: X:Tip Biçimlendirme Uzantısı.](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)  
  
- `x:Static`statik değerler üretir. Değerler, doğrudan hedef bir özelliğin değeri türü olmayan, ancak bu türe göre değerlendirilebilecek değer türü kod varlıklarından gelir. Ayrıntılar için [bkz: x:Statik Biçimlendirme Uzantısı.](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md)  
  
- `x:Null`bir özellik `null` için bir değer olarak belirtir ve öznitelikler veya özellik öğesi değerleri için kullanılabilir. Ayrıntılar için [bkz: x:Null Biçimlendirme Uzantısı.](../../../desktop-wpf/xaml-services/xnull-markup-extension.md)  
  
- `x:Array`WPF temel öğeleri ve denetim modelleri tarafından sağlanan toplama desteğinin kasıtlı olarak kullanılmadığı durumlar için XAML sözdiziminde genel dizilerin oluşturulması için destek sağlar. Ayrıntılar için [bkz: x:Dizi Biçimlendirme Uzantısı.](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)  
  
> [!NOTE]
> Önek, `x:` XAML dosyasının veya üretimin kök öğesinde, XAML dili içsellerinin tipik XAML ad alanı eşlemi için kullanılır. Örneğin, WPF uygulamaları için Visual Studio şablonları bu `x:` eşlemi kullanarak bir XAML dosyası başlatır. Kendi XAML ad alanı eşlemenizde farklı bir önek belirteci seçebilirsiniz, ancak bu belge, WPF varsayılan ad alanı veya belirli bir çerçeveyle ilgili olmayan diğer XAML ad alanlarının aksine, XAML dili için XAML ad alanının tanımlı bir parçası olan varlıkları tanımlama aracı olarak varsayılan `x:` eşlemeyi varsayar.  
  
<a name="WPF_Specific_Markup_Extensions"></a>
## <a name="wpf-specific-markup-extensions"></a>WPF'ye Özel Biçimlendirme Uzantıları  
 WPF programlamada kullanılan en yaygın biçimlendirme uzantıları, kaynak`StaticResource` başvurularını (ve) `DynamicResource`destekleyenler`Binding`ve veri bağlamayı destekleyenlerdir.  
  
- `StaticResource`zaten tanımlanmış bir kaynağın değerini ikame ederek bir özellik için bir değer sağlar. Bir `StaticResource` değerlendirme sonuçta XAML yükleme zamanında yapılır ve çalışma zamanında nesne grafiğine erişimi yoktur. Ayrıntılar için [Statik Kaynak Biçimlendirme Uzantısı'na](staticresource-markup-extension.md)bakın.  
  
- `DynamicResource`bu değeri bir kaynağa çalışma zamanı başvurusu olarak erteleyerek bir özellik için bir değer sağlar. Dinamik bir kaynak başvurusu, böyle bir kaynağa her erişilen ve çalışma zamanında nesne grafiğine erişebilen yeni bir arama zorlar. Bu erişimi elde etmek `DynamicResource` için, kavram WPF özellik sistemindebağımlılık özellikleri tarafından desteklenir ve ifadeler değerlendirilir. Bu nedenle yalnızca `DynamicResource` bir bağımlılık özelliği hedefi için kullanabilirsiniz. Ayrıntılar için [DynamicResource Biçimlendirme Uzantısı'na](dynamicresource-markup-extension.md)bakın.  
  
- `Binding`çalışma zamanında ana nesneye uygulanan veri bağlamını kullanarak bir özellik için veri bağlama değeri sağlar. Bu biçimlendirme uzantısı, veri bağlama belirtmek için önemli bir satır ara sözdizimi etkinleştirdiği için, nispeten karmaşıktır. Ayrıntılar için [Ciltİşaretleme Uzantısı'na](binding-markup-extension.md)bakın.  
  
- `RelativeSource`çalışma zamanı nesne <xref:System.Windows.Data.Binding> ağacında birkaç olası ilişkide gezinebilecek bir kaynak bilgisi sağlar. Bu, çok kullanımlı şablonlarda oluşturulan veya çevreleyen nesne ağacının tam bilgisi olmadan kod da oluşturulan bağlamalar için özel kaynak sağlar. Ayrıntılar için [Bkz. RelativeSource MarkupExtension.](relativesource-markupextension.md)  
  
- `TemplateBinding`şablonu kullanacak sınıfın nesne modeli tanımlı özelliklerinden gelen şablonlu özellikler için değerleri kullanmak için bir denetim şablonu sağlar. Başka bir deyişle, şablon tanımı içindeki özellik, yalnızca şablon uygulandıktan sonra var olan bir içeriğe erişebilir. Ayrıntılar için [ŞablonBağlayıcı Biçimlendirme Uzantısı'na](templatebinding-markup-extension.md)bakın. Pratik kullanımı hakkında daha `TemplateBinding`fazla bilgi için, [Bkz. ControlTemplates Örnek ile Şekillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap`nispeten gelişmiş bir görüntüleme senaryosu destekler. Ayrıntılar için [ColorConvertedBitmap İşaretuzantısı'na](colorconvertedbitmap-markup-extension.md)bakın.  
  
- `ComponentResourceKey`ve `ThemeDictionary` özellikle özel denetimlerle paketlenmiş kaynaklar ve temalar için kaynak aramayönlerini destekler. Daha fazla bilgi için [Bkz. ComponentResourceKey Markup Extension,](componentresourcekey-markup-extension.md) [ThemeDictionary Markup Extension](themedictionary-markup-extension.md)veya [Denetim Yazma Genel Bakış](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>
## <a name="extension-classes"></a>\*Uzantı Sınıfları  
 Hem genel XAML dili hem de WPF'ye özgü biçimlendirme uzantıları için, her biçimlendirme uzantısı `*Extension` davranışı, bir <xref:System.Windows.Markup.MarkupExtension>sınıf tan türetilen <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> ve yöntemin uygulanmasını sağlayan bir sınıf aracılığıyla bir XAML işlemcisine tanımlanır. Her uzantıdaki bu yöntem, biçimlendirme uzantısı değerlendirildiğinde döndürülen nesneyi sağlar. Döndürülen nesne genellikle biçimlendirme uzantısına geçirilen çeşitli dize belirteçleri temel alınca değerlendirilir.  
  
 Örneğin, <xref:System.Windows.StaticResourceExtension> sınıf, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> uygulanması nın istenen nesneyi döndürecek şekilde gerçek kaynak aramasının yüzey uygulamasını sağlar ve bu uygulamanın girişi kaynağı ' `x:Key`nın .' ına göre aramak için kullanılan bir dize olarak Varolan bir biçimlendirme uzantısı kullanıyorsanız, bu uygulama ayrıntılarının çoğu önemsizdir.  
  
 Bazı biçimlendirme uzantıları dize belirteç bağımsız değişkenleri kullanmayın. Bunun nedeni, statik veya tutarlı bir değer döndürmeleri veya döndürülmesi gereken değere yönelik `serviceProvider` bağlamın parametreden geçirilen hizmetlerden biri aracılığıyla kullanılabilmesidir.  
  
 Adlandırma `*Extension` deseni kolaylık ve tutarlılık içindir. Bir XAML işlemcinin bu sınıfı biçimlendirme uzantısı desteği olarak tanımlaması gerekli değildir. Codebase System.Xaml'ı içerdiği ve .NET Framework XAML Hizmetleri uygulamalarını kullandığı sürece, XAML biçimlendirme uzantısı olarak <xref:System.Windows.Markup.MarkupExtension> tanınmak için gereken tek şey bir inşaat sözdizimini elde etmek ve desteklemektir. WPF, `*Extension` örneğin <xref:System.Windows.Data.Binding>adlandırma desenini izlemeyen biçimlendirme uzantısı etkinleştirme sınıflarını tanımlar. Genellikle bunun nedeni, sınıfın saf biçimlendirme uzantısı desteğinin ötesindeki senaryoları desteklemesidir. Bu <xref:System.Windows.Data.Binding>sınıf, XAML ile ilgisi olmayan senaryolar için nesnenin yöntemlerine ve özelliklerine çalışma zamanı erişimini destekler.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Uzantısı Sınıf Başlatma Metni Yorumu  
 Biçimlendirme uzantısı adını izleyen ve hala ayraçlar içinde olan dize belirteçleri, xaml işlemci tarafından aşağıdaki yollardan biriyle yorumlanır:  
  
- Virgül her zaman tek tek belirteçlerin ayırıcısını veya sınırlayıcısını temsil eder.  
  
- Ayrı ayrı ayrılan belirteçler eşit işaretler içermiyorsa, her belirteç bir oluşturucu bağımsız değişken olarak kabul edilir. Her yapıoluşturucu parametre, bu imzatarafından beklenen tür olarak ve bu imzatarafından beklenen uygun sırada verilmelidir.  
  
    > [!NOTE]
    > Bir XAML işlemci, çift sayısının bağımsız değişken sayısıyla eşleşen oluşturucuyu aramalıdır. Bu nedenle, özel bir biçimlendirme uzantısı uyguluyorsanız, aynı bağımsız değişken sayısıile birden çok oluşturucu sağlamaz. Aynı parametre sayısına sahip birden fazla biçimlendirme uzantısı oluşturucu yolu varsa XAML işlemcinin nasıl davranış yaptığına ilişkin davranış tanımlı değildir, ancak bu durum biçimlendirme uzantısı türü tanımları.  
  
- Tek tek ayrılmış belirteçler eşit işaretler içeriyorsa, xaml işlemci önce biçimlendirme uzantısı için parametresiz oluşturucuyu çağırır. Daha sonra, her ad=değer çifti biçimlendirme uzantısı üzerinde var olan bir özellik adı ve bu özelliğe atayacak bir değer olarak yorumlanır.  
  
- Biçimlendirme uzantısında kurucu davranışı ile özellik ayar davranışı arasında paralel bir sonuç varsa, hangi davranışı kullandığınız Önemli değildir. Birden fazla ayarlanabilir özelliğe sahip biçimlendirme uzantıları için *özellik*`=`*değer* çiftlerini kullanmak daha yaygın dır, çünkü yalnızca biçimlendirmenizi daha kasıtlı hale getirir ve yanlışlıkla oluşturucu parametrelerini aktarma olasılığınız daha düşüktür. (Özellik=değer çiftleri belirttiğiniz zaman, bu özellikler herhangi bir sırada olabilir.) Ayrıca, biçimlendirme uzantısı, ayarlanan özelliklerinin her birini ayarlayan bir oluşturucu parametre sayılsa garanti etmez. Örneğin, <xref:System.Windows.Data.Binding> *özellik*`=`*değeri* formundaki uzantı aracılığıyla ayarlanan, ancak <xref:System.Windows.Data.Binding> yalnızca iki oluşturucuyu destekleyen birçok özelliği olan bir biçimlendirme uzantısıdır: parametresiz bir oluşturucu ve başlangıç yolunu ayarlayan bir uzantısı.  
  
- Gerçek bir virgül kaçış olmadan bir biçimlendirme uzantısı geçirilemez.  
  
<a name="EscapeSequences"></a>
## <a name="escape-sequences-and-markup-extensions"></a>Kaçış Dizileri ve Biçimlendirme Uzantıları  
 XAML işlemcide öznitelik işleme bir biçimlendirme uzantısı dizisinin göstergeleri olarak kıvırcık ayraçlar kullanır. Gerekirse, boş bir kıvırcık ayraç çifti ve ardından gerçek kıvırcık ayraç çiftini kullanarak bir kaçış dizisi girerek, gerekirse gerçek bir kıvırcık ayraç karakter özniteliği değeri üretmek de mümkündür. [ {} Bkz. Kaçış Sırası - Biçimlendirme Uzantısı](../../../desktop-wpf/xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>
## <a name="nesting-markup-extensions-in-xaml-usage"></a>XAML Kullanımında Biçimlendirme Uzantılarıİçleme  
 Birden çok biçimlendirme uzantıları iç içe desteklenir ve her biçimlendirme uzantısı ilk olarak en derin şekilde değerlendirilir. Örneğin, aşağıdaki kullanımı göz önünde bulundurun:  
  
```xaml  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 Bu kullanımda, `x:Static` deyim ilk değerlendirilir ve bir dize döndürür. Bu dize daha sonra `DynamicResource`için bağımsız değişken olarak kullanılır.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Biçimlendirme Uzantıları ve Özellik Öğesi Sözdizimi  
 Bir özellik öğesi değerini dolduran bir nesne öğesi olarak kullanıldığında, biçimlendirme uzantısı sınıfı XAML'de kullanılabilecek tipik bir tür destekli nesne öğesinden görsel olarak ayırt edilemez. Tipik bir nesne öğesi ve biçimlendirme uzantısı arasındaki pratik fark, biçimlendirme uzantısı ya yazılı bir değere değerlendirilir ya da bir ifade olarak ertelenmiş olmasıdır. Bu nedenle, biçimlendirme uzantısı için özellik değerlerinin olası tür hataları için mekanizmalar, geç bağlı bir özelliğin diğer programlama modellerinde nasıl ele alınmasına benzer şekilde farklı olacaktır. XAML ayrıştırıldığında ayarını attığı hedef özelliğine göre tür eşleşmesi için sıradan bir nesne öğesi değerlendirilir.  
  
 Çoğu biçimlendirme uzantıları, bir özellik öğesini doldurmak için nesne öğesi sözdiziminde kullanıldığında, içinde içerik veya başka özellik öğesi sözdizimi olmaz. Böylece nesne öğesi etiketini kapatır ve alt öğe sağlamaz. Herhangi bir nesne öğesi bir XAML işlemci tarafından karşılaşıldığında, o sınıfın oluşturucusu, ayrıştırılmış öğeden oluşturulan nesneyi anında belirleyen çağrılır. Biçimlendirme uzantısı sınıfı farklı değildir: biçimlendirme uzantınızın nesne öğesi sözdiziminde kullanılabilir olmasını istiyorsanız, parametresiz bir oluşturucu sağlamanız gerekir. Bazı varolan biçimlendirme uzantıları, etkili başlatma için belirtilmesi gereken en az bir gerekli özellik değerine sahiptir. Bu nedenle, bu özellik değeri genellikle nesne öğesi üzerinde bir özellik özniteliği olarak verilir. [XAML Ad alanında (x:) Dil Özellikleri](../../../desktop-wpf/xaml-services/namespace-language-features.md) ve [WPF XAML Uzantıları](wpf-xaml-extensions.md) başvuru sayfaları, gerekli özelliklere (ve gerekli özelliklerin adlarına) sahip biçimlendirme uzantıları not edilecektir. Başvuru sayfaları, nesne öğesi sözdizimi veya öznitelik sözdizimine belirli biçimlendirme uzantıları için izin verilip verilmediğini de not eder. Önemli bir durum [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md), bu dizinin içeriği içerik olarak etiketleme içinde belirtilmesi gerekir, çünkü öznitelik sözdizimini destekleyemez. Dizi içeriği genel nesneler olarak işlenir, bu nedenle öznitelik için varsayılan tür dönüştürücü uygulanabilir. Ayrıca, [x:Array Biçimlendirme](../../../desktop-wpf/xaml-services/xarray-markup-extension.md) `type` Uzantısı bir parametre gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [XAML Ad Uzayı (x:) Dil Özellikleri](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [WPF XAML Uzantıları](wpf-xaml-extensions.md)
- [StaticResource Biçimlendirme Uzantısı](staticresource-markup-extension.md)
- [İşaretleme Uzantısı Bağlama](binding-markup-extension.md)
- [DynamicResource Biçimlendirme Uzantısı](dynamicresource-markup-extension.md)
- [x:Type İşaretleme Uzantısı](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
