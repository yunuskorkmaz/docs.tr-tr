---
title: Bağımlılık Özelliği Değer Önceliği
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 178145b06cb937fb677b8454357bed774ed3003b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740856"
---
# <a name="dependency-property-value-precedence"></a>Bağımlılık Özelliği Değer Önceliği
<a name="introduction"></a>Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sisteminin işleyişini bir bağımlılık özelliğinin değerini nasıl etkileyebileceğini açıklar ve özellik sisteminin yönlerinin bir özelliğin etkin değeri için geçerli olduğu önceliği açıklar.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu başlığı altında, bağımlılık özelliklerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıflarında var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve okuma [bağımlılığı özelliklerine genel bakış](dependency-properties-overview.md)konusunu anladığınızı varsayar. Bu konudaki örnekleri izlemek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] anlamanız ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaların nasıl yazılacağını bilmeniz gerekir.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>WPF özellik sistemi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi, bağımlılık özelliklerinin değerinin çeşitli faktörlerle belirlenmesi, gerçek zamanlı özellik doğrulaması, geç bağlama gibi özellikleri etkinleştirmek ve değerleri için yapılan değişikliklerin ilgili özelliklerini bildirmek için güçlü bir yol sunar. diğer özellikler. Bağımlılık özelliği değerlerini belirlemede kullanılan tam sıra ve mantık makul bir şekilde karmaşıktır. Bu siparişin bilinmesi, gereksiz özellik ayarından kaçınmanıza yardımcı olur ve ayrıca bir bağımlılık özelliği değerinin ne kadar bir şekilde etkilediğine veya tahmin edildiğine ilişkin karışıklık, beklediğiniz değere neden olmuş olabilir.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Bağımlılık özellikleri birden çok yerde "set" olabilir  
 Aşağıda, aynı özelliğin (<xref:System.Windows.Controls.Control.Background%2A>) değeri etkileyebilecek üç farklı "set" işlemi olduğu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek verilmiştir.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Burada, hangi rengin uygulanacağını — kırmızı, yeşil veya mavi olacak?  
  
 Animasyon değerleri ve zorlaması dışında, yerel özellik kümeleri en yüksek önceliğe ayarlanır. Yerel olarak bir değer ayarlarsanız, herhangi bir stilin veya denetim şablonunun üzerinde bile değerin kabul olacağını belirtebilirsiniz. Örnekte, <xref:System.Windows.Controls.Control.Background%2A> yerel olarak kırmızı olarak ayarlanır. Bu nedenle, bu kapsamda tanımlanan stil, aksi halde o kapsamdaki bu türün tüm öğelerine uygulanabilecek örtülü bir stil olsa da, <xref:System.Windows.Controls.Control.Background%2A> özelliğine değer vermek için en yüksek öncelik değildir.  Bu düğme örneğinden kırmızı yerel değerini kaldırdıysanız, stilin önceliği olur ve düğme, arka plan değerini stilden elde eder.  Stil içinde, tetikler önceliklidir, bu nedenle fare onun üzerindeyken düğme mavi, aksi durumda yeşil olur.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Bağımlılık özelliği ayarı öncelik listesi  
 Bağımlılık özelliklerinin çalışma zamanı değerlerini atarken, özellik sisteminin kullandığı kesin sıra aşağıda verilmiştir. En yüksek öncelik önce listelenmiştir. Bu liste, [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)bölümünde yapılan bazı genelleştirmeler üzerinde genişletilir.  
  
1. **Özellik sistemi zorlaması.** Zorlanması hakkındaki ayrıntılar için bu konunun ilerleyen kısımlarında bulunan [zorlama, animasyon ve taban değeri](#animations) bölümüne bakın.  
  
2. **Etkin animasyonlar veya bir saklama davranışına sahip animasyonlar.** Pratik bir etkiye sahip olmak için bir özelliğin animasyonunu, bu değer yerel olarak ayarlanmış olsa bile, temel (animasyonlu) değere göre önceliğe sahip olmalıdır. Ayrıntılar için bu konunun ilerleyen kısımlarında, bkz. [zorlama, animasyon ve temel değer](#animations) .  
  
3. **Yerel değer.** Yerel bir değer, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]' de bir öznitelik veya özellik öğesi olarak ayarlanmasına veya belirli bir örneğin bir özelliği kullanılarak <xref:System.Windows.DependencyObject.SetValue%2A> API 'sine yapılan çağrıya karşılık gelen "sarmalayıcı" özelliğinin rahatlığı aracılığıyla ayarlanabilir. Bir bağlama veya kaynak kullanarak yerel bir değer ayarlarsanız, bunlar bir doğrudan değer ayarlanmış gibi önceliğe göre davranır.  
  
4. **TemplatedParent şablon özellikleri.** Bir öğenin (bir <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.DataTemplate>) bir parçası olarak oluşturulduysa bir öğe <xref:System.Windows.FrameworkElement.TemplatedParent%2A> vardır. Bunun ne zaman uygulandığı hakkında ayrıntılar için bu konunun ilerleyen kısımlarında yer alan [TemplatedParent](#templatedparent) bölümüne bakın. Şablon içinde aşağıdaki öncelik geçerlidir:  
  
    1. <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonundan tetikler.  
  
    2. <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonundaki özellik kümeleri (genellikle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri aracılığıyla).  
  
5. **Örtülü stil.** Yalnızca `Style` özelliği için geçerlidir. `Style` özelliği, bu öğenin türüyle eşleşen bir anahtara sahip herhangi bir stil kaynağı tarafından doldurulur. Bu stil kaynağı sayfada ya da uygulamada bulunmalıdır; örtük bir stil kaynağı araması, temalara devam etmez.  
  
6. **Stil Tetikleyicileri.** Sayfa veya uygulama stilleri içindeki Tetikleyiciler (Bu stiller açık veya örtük stiller olabilir, ancak varsayılan stillerden daha düşük önceliğe sahip olamaz).  
  
7. **Şablon tetikler.** Bir stilin içindeki bir şablondan veya doğrudan uygulanan bir şablonda herhangi bir tetikleyici.  
  
8. **Stil ayarlayıcıları.** Sayfa veya uygulama stilleri içindeki bir <xref:System.Windows.Setter> değerler.  
  
9. **Varsayılan (Tema) stili.** Bunun ne zaman geçerli olduğu ve tema stillerinin Tema stillerinin içindeki şablonlarla ilişkilendirilmesi hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan [varsayılan (Tema) stilleri](#themestyles) bölümüne bakın. Varsayılan bir stil içinde aşağıdaki öncelik sırası geçerlidir:  
  
    1. Tema stilindeki etkin tetikleyiciler.  
  
    2. Tema stilindeki ayarlayıcılar.  
  
10. **Devralmayı.** Birkaç bağımlılık özelliği, bir uygulama genelinde her bir öğe üzerinde özellikle ayarlanmamalıdır. bu şekilde, değerlerini üst öğeden alt öğelere alır Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).  
  
11. **Bağımlılık özelliği meta verilerinden varsayılan değer.** Belirli bir bağımlılık özelliği, ilgili özelliğin özellik sistem kaydı tarafından belirlenen varsayılan değere sahip olabilir. Ayrıca, bağımlılık özelliğini miras alan türetilmiş sınıflar, tür temelinde meta verileri geçersiz kılma (varsayılan değer dahil) seçeneğine sahiptir. Daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md) . Devralma varsayılan değerden önce denetlendiğinden, devralınan bir özellik için bir üst öğe varsayılan değeri bir alt öğeden önceliklidir.  Sonuç olarak, devralınabilir bir özellik hiçbir yerde ayarlanmamışsa, alt öğe varsayılan değeri yerine kök veya üst öğede belirtilen varsayılan değer kullanılır.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 Bir öncelik öğesi olarak TemplatedParent, doğrudan standart uygulama biçimlendirmesinde bildirdiğiniz bir öğenin herhangi bir özelliği için geçerlidir. TemplatedParent kavramı yalnızca, şablonun uygulaması aracılığıyla var olan bir görsel ağaç içindeki alt öğeler için geçerlidir. Özellik sistemi bir değer için <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonunda arama yaptığında, bu öğeyi oluşturan şablonda arama yapılır. <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablondaki özellik değerleri genellikle alt öğe üzerinde yerel bir değer olarak ayarlanmış gibi davranır, ancak şablonlar potansiyel olarak paylaşıldığından bu, yerel değere karşı daha düşük önceliğe sahiptir. Ayrıntılar için bkz. <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Style özelliği  
 Daha önce açıklanan arama sırası, biri hariç tüm olası bağımlılık özellikleri için geçerlidir: <xref:System.Windows.FrameworkElement.Style%2A> özelliği. <xref:System.Windows.FrameworkElement.Style%2A> özelliği, tek başına stillenemez ve bu nedenle 5 ile 8 arasındaki öncelik öğeleri uygulanmaz. Ayrıca, hareketlendirilen veya zorlama <xref:System.Windows.FrameworkElement.Style%2A> önerilmez (ve hareketlendirmek <xref:System.Windows.FrameworkElement.Style%2A> özel bir animasyon sınıfı gerektirir). Bu, <xref:System.Windows.FrameworkElement.Style%2A> özelliğinin ayarlanmış olabileceği üç yolu bırakır:  
  
- **Açık stil.** <xref:System.Windows.FrameworkElement.Style%2A> özelliği doğrudan ayarlanır. Çoğu senaryoda stil satır içi olarak tanımlanmamıştır, ancak bunun yerine açık anahtara göre kaynak olarak başvurulur. Bu durumda, Style özelliği yerel bir değer, öncelik öğesi 3 gibi davranır.  
  
- **Örtülü stil.** <xref:System.Windows.FrameworkElement.Style%2A> özelliği doğrudan ayarlanmadı. Ancak <xref:System.Windows.FrameworkElement.Style%2A>, kaynak arama dizisindeki (sayfa, uygulama) bir düzeyde bulunur ve stilin uygulanacağı türle eşleşen bir kaynak anahtarı kullanılarak anahtarlanır. Bu durumda <xref:System.Windows.FrameworkElement.Style%2A> özelliği, öğe 5 olarak dizide tanımlanan bir önceliğe göre davranır. Bu durum, <xref:System.Windows.FrameworkElement.Style%2A> özelliğinde <xref:System.Windows.DependencyPropertyHelper> kullanılarak ve sonuçlarda <xref:System.Windows.BaseValueSource.ImplicitStyleReference> aranırken algılanabilir.  
  
- **Varsayılan stil**, **Tema stili** olarak da bilinir. <xref:System.Windows.FrameworkElement.Style%2A> özelliği doğrudan ayarlanmamış ve aslında çalışma zamanına kadar `null` olarak okunacak. Bu durumda, stil, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Presentation altyapısının parçası olan çalışma zamanı teması değerlendirmesinden gelir.  
  
 Temalarda olmayan örtük stiller için, türün tam olarak eşleşmesi gerekir-bir `MyButton` `Button`türetilmiş bir sınıf örtük olarak `Button`için stil kullanmayacak.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Varsayılan (Tema) stilleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile birlikte gelen her denetim için varsayılan bir stil vardır. Bu varsayılan stil potansiyel olarak temaya göre farklılık gösterir. Bu, varsayılan stilin bazen Tema stili olarak adlandırılmasıdır.  
  
 Bir denetim için varsayılan bir stil içinde bulunan en önemli bilgiler, <xref:System.Windows.Controls.Control.Template%2A> özelliği için bir ayarlayıcı olarak tema stilinde bulunan denetim şablonudur. Varsayılan stillerden şablon yoksa, özel bir stilin parçası olmayan bir denetimin hiçbir görsel görünümü yoktur. Varsayılan stildeki şablon, her denetimin temel bir yapı için görsel görünümünü verir ve ayrıca şablonun görsel ağacında ve ilgili denetim sınıfında tanımlanan özellikler arasındaki bağlantıları tanımlar. Her denetim, şablonu tamamen değiştirmeden denetimin görsel görünümünü etkileyebilecek bir özellikler kümesi sunar. Örneğin, bir <xref:System.Windows.Controls.Primitives.ScrollBar>bileşeni olan <xref:System.Windows.Controls.Primitives.Thumb> denetimin varsayılan görsel görünümünü göz önünde bulundurun.  
  
 <xref:System.Windows.Controls.Primitives.Thumb>, bazı özelleştirilebilir özelliklere sahiptir. Bir <xref:System.Windows.Controls.Primitives.Thumb> varsayılan şablonu, bir eğim görünümü oluşturmak için birkaç iç içe <xref:System.Windows.Controls.Border> bileşeni olan temel bir yapı/görsel ağacı oluşturur. Şablonun bir parçası olan bir özelliğin <xref:System.Windows.Controls.Primitives.Thumb> sınıfı tarafından özelleştirilmesini sağlamak istiyorsanız, bu özellik şablon içinde bir [TemplateBinding](templatebinding-markup-extension.md)tarafından kullanıma sunulmalıdır. <xref:System.Windows.Controls.Primitives.Thumb>durumda, bu kenarlıkların çeşitli özellikleri <xref:System.Windows.Controls.Border.Background%2A> veya <xref:System.Windows.Controls.Border.BorderThickness%2A>gibi özelliklere bir şablon bağlamasını paylaşır. Ancak bazı diğer özellikler ya da görsel düzenlemeler denetim şablonuna sabit olarak kodlanmıştır veya doğrudan temadan gelen değerlere bağlanır ve tüm şablonu değiştirmek için kısa bir süre değiştirilemez. Genellikle, bir özellik şablonlu bir üst öğeden geliyorsa ve şablon bağlama tarafından gösterilmediği için, bu, hedeflemenin kolay bir yolu olmadığından stiller tarafından ayarlanamaz. Ancak bu özellik, uygulanan şablondaki özellik değeri devralmasından veya varsayılan değere göre etkilenebilir.  
  
 Tema stilleri, tanımlarındaki anahtar olarak bir tür kullanır. Ancak, Temalar belirli bir öğe örneğine uygulandığında, bu tür için Temalar araması, bir denetimdeki <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> özelliği denetlenerek gerçekleştirilir. Bu, örtük stiller olduğundan, değişmez değer türünü kullanmanın aksine. <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> değeri, uygulayıcının onu değiştirmese bile türetilmiş sınıflara devralınır (özelliği değiştirmenin amaçlanan yolu, özellik düzeyinde geçersiz kılınmıyor, ancak bunun yerine özellik meta verilerinde varsayılan değerini değiştirin). Bu yöneltme, temel sınıfların, başka bir stile sahip olmayan türetilmiş öğeler için Tema stillerini tanımlamasına olanak sağlar (veya daha önemlisi, bu stil içinde bir şablonu yoktur ve bu nedenle hiçbir varsayılan görsel görünümü yoktur). Bu nedenle, <xref:System.Windows.Controls.Button> `MyButton` türetebilirsiniz ve <xref:System.Windows.Controls.Button> varsayılan şablonu almaya devam edebilirsiniz. `MyButton` denetim yazarınızı yaptıysanız ve farklı bir davranış istediyseniz, farklı bir anahtar döndürmek için `MyButton` <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> bağımlılık özelliği meta verilerini geçersiz kılabilir ve sonra `MyButton` için şablon dahil ilgili tema stillerini tanımlayabilirsiniz. `MyButton` denetibir şekilde paketetmeniz gerekir. Temalar, stiller ve denetim yazma hakkında daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dinamik kaynak başvuruları ve bağlama  
 Dinamik kaynak başvuruları ve bağlama işlemleri, ayarlandığı konumun önceliğine göre yapılır. Örneğin, yerel bir değere uygulanan dinamik bir kaynak, öncelik öğesi 3 ' e göre hareket eder, bir tema stili içindeki bir özellik ayarlayıcısı için bağlama, öncelik öğesi 9 ' da uygulanır ve bu şekilde devam eder. Dinamik kaynak başvurularının ve bağlamanın her ikisi de uygulamanın çalışma zamanı durumundan değerleri alabilmesi gerektiğinden, bu, belirli bir özellik için özellik değeri önceliğini belirleme işleminin de çalışma zamanına göre uzanıyor olması gerekir.  
  
 Dinamik kaynak başvuruları, özellik sisteminin bir parçası olarak tamamen konuşmaz, ancak yukarıda listelenen sırayla etkileşimde bulunan bir arama sırası vardır. Bu öncelik [xaml kaynaklarında](../../../desktop-wpf/fundamentals/xaml-resources-define.md)daha kapsamlı olarak belgelenmiştir. Bu önceliğin temel toplamı: öğe, sayfa kökü, uygulama, tema, sistem.  
  
 Dinamik kaynaklar ve bağlamalar, ayarlandığı yere öncelik kazanır, ancak değer ertelenir. Bunun bir sonucu olarak, dinamik bir kaynak ayarlarsanız veya yerel bir değere bağlıyorsanız, yerel değerde yapılan herhangi bir değişiklik dinamik kaynağı veya bağlama tamamen değiştirilir. Yerel olarak ayarlanan değeri temizlemek için <xref:System.Windows.DependencyObject.ClearValue%2A> yöntemini çağırsanız bile, dinamik kaynak veya bağlama geri yüklenmez. Aslında, dinamik kaynak veya bağlama (değişmez değer yerel değeri olmadan) olan bir özellikte <xref:System.Windows.DependencyObject.ClearValue%2A> çağırırsanız, <xref:System.Windows.DependencyObject.ClearValue%2A> çağrısı tarafından temizlenir.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> yöntemi bir özelliği ayarlamaya yönelik başka bir yoldur, ancak öncelik sırasına göre değildir. Bunun yerine, <xref:System.Windows.DependencyObject.SetCurrentValue%2A> bir özelliğin değerini, önceki bir değerin kaynağının üzerine yazmadan değiştirmenize olanak sağlar. Bu değere bir yerel değerin önceliği vermeden bir değer ayarlamak istediğiniz zaman <xref:System.Windows.DependencyObject.SetCurrentValue%2A> kullanabilirsiniz. Örneğin, bir özellik bir tetikleyici tarafından ayarlanır ve ardından <xref:System.Windows.DependencyObject.SetCurrentValue%2A>aracılığıyla başka bir değer atanırsa, özellik sistemi tetikleyiciyi hala uyar ve tetikleyici eylemi gerçekleşirse özellik değişir. <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, özelliğin değerini daha yüksek önceliğe sahip bir kaynak vermeden değiştirmenize olanak sağlar. Benzer şekilde, bir özelliğin değerini bir bağlamanın üzerine yazmadan değiştirmek için <xref:System.Windows.DependencyObject.SetCurrentValue%2A> kullanabilirsiniz.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Zorlama, animasyonlar ve taban değeri  
 Zorlama ve animasyon her ikisi de bu SDK 'nın tamamında "temel değer" olarak adlandırılmış bir değer üzerinde çalışır. Temel değer bu nedenle, öğe 2 ' ye ulaşılana kadar öğelerin yukarı hesaplanmasıyla belirlenen değer belirlenir.  
  
 Animasyon için, bu animasyon, belirli davranışlar için hem "Kimden" hem de "to" belirtmezse ya da bir animasyon tamamlandığında temel değere geri döndürüyorsa, bir animasyon için temel değer bir etkiye sahip olabilir. Bunu uygulamada görmek için [from, to ve By animasyon hedefi değerleri örneğini](https://go.microsoft.com/fwlink/?LinkID=159988)çalıştırın. Örnekteki dikdörtgen yüksekliğinin yerel değerlerini ayarlamayı deneyin. Örneğin, başlangıçtaki yerel değer animasyondaki herhangi bir "from" adından farklı olacak. Animasyonların "Kimden" değerlerini kullanarak hemen başladığını ve temel değeri başladıktan sonra istediğinizi göreceksiniz. Animasyon, durdurma <xref:System.Windows.Media.Animation.FillBehavior>belirterek, animasyondan önce bulunan değere geri dönmek için belirtebilir. Daha sonra, temel değer belirleme için normal öncelik kullanılır.  
  
 Birden çok animasyon tek bir özelliğe uygulanabilir, bu animasyonların her biri değer önceliğinde farklı noktalarda tanımlanmış olabilir. Ancak, bu animasyonlar, animasyonu daha yüksek önceliğe uygulamak yerine, büyük olasılıkla kendi değerlerini öngörür. Bu, animasyonların tam olarak nasıl tanımlandığına ve hareketlendirilen değerin türüne bağlıdır. Hareketlendirilen özellikler hakkında daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).  
  
 Zorlama, en yüksek düzeyde uygulanır. Zaten çalışan bir animasyon de değer zorya tabidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mevcut olan bağımlılık özelliklerinin yerleşik bir zorlaması vardır. Özel bir bağımlılık özelliği için, bir <xref:System.Windows.CoerceValueCallback> yazarak ve geri aramayı, özelliği oluştururken meta verilerin bir parçası olarak geçirerek özel bir bağımlılık özelliği için zorlama davranışını tanımlarsınız. Ayrıca, türetilmiş bir sınıftaki bu özellikte bulunan meta verileri geçersiz kılarak varolan özelliklerin zorlama davranışını geçersiz kılabilirsiniz. Zorlama, temel değeri ile etkileşime girer ve bu kısıtlamalar zaman içinde mevcut olduğu için, zordaki kısıtlamaların uygulandığı şekilde uygulanır, ancak temel değer hala tutulur. Bu nedenle, zorlanacak kısıtlamalar daha sonra yükseltilmemiş ise, zorlama bu temel değere mümkün olan en yakın değeri döndürür ve potansiyel olarak bir özellikte zorlama etkisi, tüm kısıtlamalar yükseltilmemiş olur almaz. Zorlama davranışı hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Tetikleyici davranışları  
 Denetimler genellikle tetikleyici davranışlarını Temalar içinde varsayılan stilinin bir parçası olarak tanımlar. Denetimlerde yerel özellikleri ayarlamak, tetikleyicilerin görsel veya davranışsal Kullanıcı odaklı olaylara yanıt verebilmesini engelleyebilir. Bir özellik tetikleyicisinin en yaygın kullanımı, <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>gibi denetim veya durum özellikleri içindir. Örneğin, varsayılan olarak bir <xref:System.Windows.Controls.Button> devre dışı bırakıldığında (<xref:System.Windows.UIElement.IsEnabled%2A> için tetikleyici `false`), tema stilindeki <xref:System.Windows.Controls.Control.Foreground%2A> değeri denetimin "gri" görünmesine neden olur. Ancak, yerel bir <xref:System.Windows.Controls.Control.Foreground%2A> değeri ayarladıysanız, bu özellik tarafından tetiklenen senaryoda bile, bu normal gri çıkış rengi yerel özellik ayarlamış olduğunuz öncelik sırasına göre geçersiz kılınır. Tema düzeyi tetikleyici davranışları olan özelliklerin değerlerini ayarlamasından ve bu denetim için amaçlanan kullanıcı deneyimi ile etkilenmemesi engel olmadığından emin olun.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue ve value önceliği  
 <xref:System.Windows.DependencyObject.ClearValue%2A> yöntemi, bir öğesi üzerinde ayarlanmış bir bağımlılık özelliğinden yerel olarak uygulanan bir değeri temizlemek için bir yol sağlar. Ancak, <xref:System.Windows.DependencyObject.ClearValue%2A> çağırmak, varsayılan olarak, özellik kaydı sırasında meta verilerde kurulduğu şekilde yeni bir etkin değer olduğundan emin değildir. Değer önceliğinde diğer tüm katılımcılar hala etkin. Öncelik sırasından yalnızca yerel olarak ayarlanan değer kaldırılmıştır. Örneğin, bu özelliğin aynı zamanda bir tema stili tarafından ayarlandığı bir özellikte <xref:System.Windows.DependencyObject.ClearValue%2A> çağırırsanız, tema değeri meta veri tabanlı varsayılan değer yerine yeni değer olarak uygulanır. Tüm özellik değeri katılımcıları ' ni işlemin dışına almak ve değeri kayıtlı meta veri varsayılana ayarlamak istiyorsanız, bağımlılık özelliği meta verilerini sorgulayarak bu varsayılan değeri tanımlanabilir olarak elde edebilir ve ardından varsayılan değeri yerel olarak kullanabilirsiniz özelliğini <xref:System.Windows.DependencyObject.SetValue%2A>çağrısı ile ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliği Geri Aramaları ve Doğrulama](dependency-property-callbacks-and-validation.md)
