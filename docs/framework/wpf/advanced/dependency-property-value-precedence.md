---
title: Bağımlılık Özelliği Değer Önceliği
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 1d7c644c7f7581a96ffff1a0fe1fcf2adfe071e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186142"
---
# <a name="dependency-property-value-precedence"></a>Bağımlılık Özelliği Değer Önceliği
<a name="introduction"></a>Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sisteminin işleyişinin bir bağımlılık özelliğinin değerini nasıl etkileyebileceğini açıklar ve özellik sisteminin hangi yönlerinin bir özelliğin etkin değerine uyguladığı önceliği açıklar.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliklerini sınıflardaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varolan bağımlılık özelliklerinin tüketici perspektifinden anladığınızı ve Bağımlılık Özellikleri Genel [Bakış'ı](dependency-properties-overview.md)okuduğunuzu varsayar. Bu konudaki örnekleri takip etmek için, uygulamaları nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazacağını da anlamalı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve bilmelidir.  
  
<a name="intro"></a>
## <a name="the-wpf-property-system"></a>WPF Özellik Sistemi  
 Özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistemi, bağımlılık özelliklerinin değerinin çeşitli etkenler tarafından belirlenmesi için güçlü bir yol sunar, bu da gerçek zamanlı özellik doğrulama, geç bağlama gibi özellikleri etkinleştirerek ve ilgili özellikleri diğer özellikler için değerlere ilişkin değişikliklere bildirmektedir. Bağımlılık özelliği değerlerini belirlemek için kullanılan tam sıra ve mantık oldukça karmaşıktır. Bu siparişi bilmek gereksiz özellik ayarı önlemek yardımcı olacaktır ve aynı zamanda tam olarak neden bazı girişimi etkilemek veya bir bağımlılık özelliği değeri tahmin neden beklediğiniz değer sonuçlanan sonuçlanmadı üzerinde karışıklığı temizlemek olabilir.  
  
<a name="multiple_sets"></a>
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Bağımlılık Özellikleri Birden Çok Yerde "Ayarlan" Olabilir  
 Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı özelliğin<xref:System.Windows.Controls.Control.Background%2A>( ) değeri etkileyebilecek üç farklı "küme" işlemi ne rendelenmiştir.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Burada, kırmızı, yeşil veya mavi hangi rengin geçerli olacağını bekliyorsunuz?  
  
 Animasyonlu değerler ve zorlama dışında, yerel özellik kümeleri en yüksek önceliğe göre ayarlanır. Yerel olarak bir değer belirlerseniz, herhangi bir stil veya denetim şablonlarının üzerinde bile değerin onurlandırılmasını bekleyebilirsiniz. Burada örnekte, <xref:System.Windows.Controls.Control.Background%2A> yerel olarak Red olarak ayarlanır. Bu nedenle, bu kapsamda tanımlanan stil, aksi takdirde bu kapsamda bu tür tüm öğeler için geçerli olacak örtük bir <xref:System.Windows.Controls.Control.Background%2A> stil olsa da, özellik değerini vermek için en yüksek öncelik değildir.  Kırmızı'nın yerel değerini bu Düğme örneğinden kaldırdıysanız, stilin önceliği olur ve düğme stilden Arka Plan değerini alır.  Stil içinde, tetikleyiciler önceliklidir, bu nedenle fare üzerindeyse düğme mavi, aksi takdirde yeşil olacaktır.  
  
<a name="listing"></a>
## <a name="dependency-property-setting-precedence-list"></a>Bağımlılık Özelliği Ayarı Öncelik Listesi  
 Aşağıda, özellik sisteminin bağımlılık özelliklerinin çalışma zamanı değerlerini atarken kullandığı kesin sıra dır. En yüksek öncelik önce listelenir. Bu liste, [Bağımlılık Özellikleri Genel Bakış](dependency-properties-overview.md)yapılan bazı genellemeler genişletir.  
  
1. **Özellik sistemi zorlama.** Zorlama yla ilgili ayrıntılar için, bu konuda daha sonra [Zorlama, Animasyon ve Temel Değer'e](#animations) bakın.  
  
2. **Etkin animasyonlar veya Bekleme davranışı içeren animasyonlar.** Herhangi bir pratik etkiye sahip olmak için, bir özelliğin animasyonu, bu değer yerel olarak ayarlanmış olsa bile, temel (animasyonsuz) değerden önceliğe sahip olmalıdır. Ayrıntılar için, bu konunun ilerleyen saatlerinde [Zorlama, Animasyon ve Temel Değer'e](#animations) bakın.  
  
3. **Yerel değer.** Yerel bir değer, "sarmalayıcı" özelliğinin kolaylığı yoluyla ayarlanabilir, bu da belirli bir örneğin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]özelliğini kullanarak <xref:System.Windows.DependencyObject.SetValue%2A> API'ye yapılan bir çağrıda bir öznitelik veya özellik öğesi olarak ayarlanmasına eşittir. Bir bağlama veya kaynak kullanarak yerel bir değer ayarlarsanız, bunların her hareketi doğrudan bir değer ayarlanmış gibi önceliklidir.  
  
4. **TemplatedParent şablon özellikleri.** Bir öğenin <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonun bir parçası olarak oluşturulmuş <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.DataTemplate>sa'sı vardır (a veya). Bunun ne zaman uygulanacağı hakkında ayrıntılı bilgi için, daha sonra bu konuda [TemplatedParent'](#templatedparent) a bakın. Şablon içinde aşağıdaki öncelik geçerlidir:  
  
    1. <xref:System.Windows.FrameworkElement.TemplatedParent%2A> Şablondan tetikleyiciler.  
  
    2. Şablondaki özellik kümeleri (genellikle öznitelikler aracılığıyla). [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.FrameworkElement.TemplatedParent%2A>  
  
5. **Örtük stil.** Yalnızca `Style` özellik için geçerlidir. Özellik, `Style` bu öğenin türüyle eşleşen bir anahtarla herhangi bir stil kaynağı tarafından doldurulur. Bu stil kaynağı sayfada veya uygulamada bulunmalıdır; örtülü bir stil kaynağı için arama temalar içine devam etmez.  
  
6. **Stil tetikleyicileri.** Sayfa veya uygulama stilleri içindeki tetikleyiciler (bu stiller açık veya örtülü stiller olabilir, ancak daha düşük önceliğe sahip varsayılan stiller den olmayabilir).  
  
7. **Şablon tetikleyiciler.** Bir stil içindeki şablondan gelen tetikleyiciler veya doğrudan uygulanan şablon.  
  
8. **Stil belirleyiciler.** Sayfa veya <xref:System.Windows.Setter> uygulamadan bir içindeki stillerden gelen değerler.  
  
9. **Varsayılan (tema) stili.** Bunun ne zaman uygulandığı ve tema stillerinin tema stilleriiçindeki şablonlarla nasıl ilişkili olduğu hakkında ayrıntılı bilgi için, bu konunun ilerleyen saatlerinde [Varsayılan (Tema) Stilleri'ne](#themestyles) bakın. Varsayılan bir stil içinde, aşağıdaki öncelik sırası uygulanır:  
  
    1. Tema stilinde etkin tetikleyiciler.  
  
    2. Tema stilinde ayarlar.  
  
10. **Devralma.** Birkaç bağımlılık özellikleri, değerlerini üst öğeden alt öğelere devralır, böylece uygulama boyunca her öğeüzerinde özel olarak ayarlanmamalıdır. Ayrıntılar için [Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)  
  
11. **Bağımlılık özelliği meta verilerinden varsayılan değer.** Verilen herhangi bir bağımlılık özelliği, o özelliğin özellik sistem kaydı tarafından belirlenen varsayılan değere sahip olabilir. Ayrıca, bağımlılık özelliği devralan türemiş sınıflar, bu meta verileri (varsayılan değer dahil) her tür bazında geçersiz kılma seçeneğine sahiptir. Daha fazla bilgi için [Bağımlılık Özelliği Meta verilerine](dependency-property-metadata.md) bakın. Devralma varsayılan değerden önce denetlendirilen için, devralınan bir özellik için, üst öğe varsayılan değeri bir alt öğeden önce gelir.  Sonuç olarak, devralılabilir bir özellik herhangi bir yerde ayarlanmamışsa, alt öğe varsayılan değeri yerine kök veya üst öğeüzerinde belirtilen varsayılan değer kullanılır.  
  
<a name="templatedparent"></a>
## <a name="templatedparent"></a>Templatedparent  
 Öncelik öğesi olarak TemplatedParent, doğrudan standart uygulama biçimlendirmesinde beyan ettiğiniz bir öğenin herhangi bir özelliği için geçerli değildir. TemplatedParent kavramı yalnızca şablonun uygulanması yla ortaya çıkan görsel bir ağaçtaki alt öğeler için vardır. Özellik sistemi şablonu <xref:System.Windows.FrameworkElement.TemplatedParent%2A> bir değer için aradığında, bu öğeyi oluşturan şablonu arar. <xref:System.Windows.FrameworkElement.TemplatedParent%2A> Şablondaki özellik değerleri genellikle alt öğeüzerinde yerel bir değer olarak ayarlanmış gibi davranır, ancak şablonlar büyük ölçüde paylaşıldığından yerel değere karşı bu daha küçük öncelik vardır. Ayrıntılar için bkz. <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>
## <a name="the-style-property"></a>Stil Özelliği  
 Daha önce açıklanan arama sırası, biri hariç tüm olası <xref:System.Windows.FrameworkElement.Style%2A> bağımlılık özellikleri için geçerlidir: özellik. Özellik, <xref:System.Windows.FrameworkElement.Style%2A> kendisi tarz olamaz benzersizdir, bu nedenle öncelik öğeleri 5 ile 8 geçerli değildir. Ayrıca, animasyon veya zorlama <xref:System.Windows.FrameworkElement.Style%2A> önerilmez (ve animasyon özel bir <xref:System.Windows.FrameworkElement.Style%2A> animasyon sınıfı gerektirir). Bu, özelliğin <xref:System.Windows.FrameworkElement.Style%2A> ayarlanabileceği üç yol bırakır:  
  
- **Açık stil.** Tesis <xref:System.Windows.FrameworkElement.Style%2A> doğrudan ayarlanır. Çoğu senaryoda, stil satır içinde tanımlanmaz, ancak bunun yerine açık anahtarla kaynak olarak başvurur. Bu durumda Stil özelliğinin kendisi yerel bir değer, öncelik öğesi 3 gibi davranır.  
  
- **Örtük stil.** Özellik <xref:System.Windows.FrameworkElement.Style%2A> doğrudan ayarlanmaz. Ancak, <xref:System.Windows.FrameworkElement.Style%2A> kaynak arama dizisinde (sayfa, uygulama) bir düzeyde var ve stil uygulanacak türeşleşen bir kaynak anahtarı kullanılarak anahtarlanır. Bu durumda, <xref:System.Windows.FrameworkElement.Style%2A> özelliğin kendisi, madde 5 olarak sırayla tanımlanan bir önceki ile hareket eder. Bu durum <xref:System.Windows.DependencyPropertyHelper> <xref:System.Windows.FrameworkElement.Style%2A> özelliği ne karşı kullanarak ve <xref:System.Windows.BaseValueSource.ImplicitStyleReference> sonuçlarda arayarak tespit edilebilir.  
  
- **Varsayılan stil**, tema stili olarak da **bilinir.** Özellik <xref:System.Windows.FrameworkElement.Style%2A> doğrudan ayarlanmaz ve aslında çalışma `null` süresine kadar olarak okunur. Bu durumda, stil [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunu altyapısının bir parçası olan çalışma zamanı tema değerlendirmesinden gelir.  
  
 Temalarda olmayan örtük stiller için, `MyButton` `Button` `Button`tür tam olarak eşleşmelidir - türetilmiş bir sınıf için örtülü olarak bir stil kullanmaz.  
  
<a name="themestyles"></a>
## <a name="default-theme-styles"></a>Varsayılan (Tema) Stilleri  
 Gemilerin varsayılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stili olan her denetimin bir tarzı vardır. Bu varsayılan stil potansiyel olarak temaya göre değişir, bu nedenle bu varsayılan stil bazen bir tema stili olarak adlandırılır.  
  
 Denetim için varsayılan stil içinde bulunan en önemli bilgi, <xref:System.Windows.Controls.Control.Template%2A> özelliği için ayarlayıcı olarak tema stilinde bulunan denetim şablonudur. Varsayılan stillerden şablon yoksa, özel bir stilin parçası olarak özel şablonu olmayan bir denetimin hiç görsel görünümü olmazdı. Varsayılan stildeki şablon, her denetimin görsel görünümünü temel bir yapı verir ve ayrıca şablonun görsel ağacında tanımlanan özellikler ile ilgili denetim sınıfı arasındaki bağlantıları tanımlar. Her denetim, şablonu tamamen değiştirmeden denetimin görsel görünümünü etkileyebilen bir dizi özelliği ortaya çıkarır. Örneğin, bir <xref:System.Windows.Controls.Primitives.Thumb> denetimin varsayılan görsel görünümünü göz önünde <xref:System.Windows.Controls.Primitives.ScrollBar>bulundurun.  
  
 A'nın <xref:System.Windows.Controls.Primitives.Thumb> belirli özelleştirilebilir özellikleri vardır. Bir varsayılan şablon, bir dikin görünüm oluşturmak için <xref:System.Windows.Controls.Border> birkaç iç içe bileşenleri ile temel bir yapı / görsel ağaç <xref:System.Windows.Controls.Primitives.Thumb> oluşturur. Şablonun bir parçası olan bir <xref:System.Windows.Controls.Primitives.Thumb> özelliğin sınıf tarafından özelleştirme için açığa çıkarılması amaçlanıyorsa, bu özelliğin şablon içinde bir [TemplateBinding](templatebinding-markup-extension.md)tarafından ortaya çıkarılması gerekir. <xref:System.Windows.Controls.Primitives.Thumb>Durumunda, bu sınırların çeşitli özellikleri gibi <xref:System.Windows.Controls.Border.Background%2A> özelliklere bağlayıcı bir şablon u yitimi. <xref:System.Windows.Controls.Border.BorderThickness%2A> Ancak, diğer bazı özellikler veya görsel düzenlemeler denetim şablonuna sabit kodlanır veya doğrudan temadan gelen değerlere bağlıdır ve şablonun tamamını değiştirmek ten kısa sürede değiştirilemez. Genellikle, bir özellik şablonlu bir üst öğeden geliyorsa ve şablon bağlama tarafından açıklanmıyorsa, onu hedeflemenin kolay bir yolu olmadığından stiller tarafından ayarlanamaz. Ancak bu özellik, uygulanan şablondaki özellik değeri devralma veya varsayılan değerden yine de etkilenebilir.  
  
 Tema stilleri tanımlarında anahtar olarak bir tür kullanır. Ancak, temalar belirli bir öğe örneğine uygulandığında, bu tür <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> için temalar arama bir denetim üzerinde özellik denetleyerek gerçekleştirilir. Bu, örtük stillerin kullandığı gibi, gerçek Türü kullanmanın aksinedir. <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> Uygulayıcı değiştirmemiş olsa bile türetilmiş sınıflara devralınan değer (özelliği değiştirmenin amaçlanan yolu, özelliği geçersiz kılmak için değil, bunun yerine özellik meta verilerindeki varsayılan değerini değiştirmektir). Bu yönlendirme, temel sınıfların, başka bir tarzı olmayan türemiş öğeleriçin tema stillerini tanımlamasına olanak tanır (veya daha da önemlisi, bu stiliçinde şablon yoktur ve böylece varsayılan görsel görünüme sahip olmaz). Böylece, ve `MyButton` türetmek <xref:System.Windows.Controls.Button> hala <xref:System.Windows.Controls.Button> varsayılan şablon ualırsınız. Denetimin yazarı ysanız `MyButton` ve farklı bir davranış istiyorsanız, farklı bir anahtar döndürmek <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> `MyButton` için bağımlılık özelliği meta verilerini geçersiz kılabilir ve ardından `MyButton` denetiminizi `MyButton` paketlemeniz gereken şablonda şablon u dahil olmak üzere ilgili tema stillerini tanımlayabilirsiniz. Temalar, stiller ve denetim yazma hakkında daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)  
  
<a name="resources"></a>
## <a name="dynamic-resource-references-and-binding"></a>Dinamik Kaynak Başvuruları ve Bağlama  
 Dinamik kaynak başvuruları ve bağlama işlemleri, ayarlandıkları konumun önceliğine saygı duyar. Örneğin, yerel bir değere uygulanan dinamik bir kaynak, öncelik öğesi 3'e göre hareket eder, bir tema stilindeki özellik ayarlayıcısı için bağlayıcı, öncelik öğesi 9'da ve benzeri bir şekilde uygulanır. Dinamik kaynak başvuruları ve bağlama her ikisi de uygulamanın çalışma süresi durumundan değerleri elde etmek gerekir, bu belirli bir özellik için özellik değeri önceliği belirleme fiili süreci de çalışma süresi içine uzanır gerektirir.  
  
 Dinamik kaynak başvuruları kesinlikle özellik sisteminin bir parçası konuşan değildir, ancak yukarıda listelenen sıra ile etkileşime kendi bir arama sırası var. Bu öncelik [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)daha ayrıntılı olarak belgelenmiştir. Bu önceliğin temel toplamı: sayfa kökü, uygulama, tema, sistem öğesi.  
  
 Dinamik kaynaklar ve bağlamalar ayarlandıkları yerin önceliğidir, ancak değer ertelenir. Bunun bir sonucu, dinamik bir kaynak ayarlarsanız veya yerel bir değere bağlanırsanız, yerel değerdeki herhangi bir değişiklik dinamik kaynağın veya bağlamanın tamamen yerini alır. Yerel olarak ayarlanan değeri temizlemek için <xref:System.Windows.DependencyObject.ClearValue%2A> yöntemi çağırsanız bile, dinamik kaynak veya bağlama geri yüklenmez. Aslında, dinamik bir <xref:System.Windows.DependencyObject.ClearValue%2A> kaynağa sahip veya yerinde bağlayıcı (gerçek yerel değeri olmayan) bir özelliği <xref:System.Windows.DependencyObject.ClearValue%2A> çağırırsanız, bunlar da çağrı tarafından temizlenir.  
  
<a name="setcurrentvalue"></a>
## <a name="setcurrentvalue"></a>SetCurrentValue  
 Yöntem, <xref:System.Windows.DependencyObject.SetCurrentValue%2A> bir özelliği ayarlamanın başka bir yoludur, ancak öncelik sırasına göre değildir. Bunun <xref:System.Windows.DependencyObject.SetCurrentValue%2A> yerine, önceki bir değerin kaynağını abartmadan bir özelliğin değerini değiştirmenize olanak tanır. Bu değere yerel bir değerin önceliğini vermeden değer ayarlamak istediğiniz zaman kullanabilirsiniz. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Örneğin, bir özellik bir tetikleyici tarafından ayarlanır ve <xref:System.Windows.DependencyObject.SetCurrentValue%2A>sonra başka bir değer üzerinden atanmışsa , özellik sistemi yine de tetikleyiciye saygı duyar ve tetikleyicinin eylemi gerçekleşirse özellik değişir. <xref:System.Windows.DependencyObject.SetCurrentValue%2A>daha yüksek bir önceliğe sahip bir kaynak vermeden özelliğin değerini değiştirmenizi sağlar. Aynı şekilde, bir <xref:System.Windows.DependencyObject.SetCurrentValue%2A> bağlama üzerine yazmadan bir özelliğin değerini değiştirmek için kullanabilirsiniz.  
  
<a name="animations"></a>
## <a name="coercion-animations-and-base-value"></a>Zorlama, Animasyonlar ve Temel Değer  
 Zorlama ve animasyon, bu SDK boyunca "temel değer" olarak nitelendirilen bir değer üzerinde hareket eder. Böylece temel değer, madde 2'ye ulaşılıncaya kadar maddelerdeki yukarı doğru değerlendirilerek hangi değer belirlenirse belirlenmez.  
  
 Animasyon için, bu animasyon belirli davranışlar için hem "From" hem de "To" belirtmezse veya animasyon tamamlandığında temel değere kasıtlı olarak geri dönüyorsa, temel değer animasyondeğeri üzerinde etkili olabilir. Bunu uygulamada görmek [için, From, To ve By Animasyon Hedef Değerleri Örneğini](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)çalıştırın. Örnekteki dikdörtgen yüksekliğinin yerel değerlerini ayarlamayı deneyin, örneğin ilk yerel değeri animasyondaki herhangi bir "Gönderen"den farklıdır. Animasyonların "Gönderen" değerlerini kullanarak hemen başladığını ve başladıktan sonra temel değeri değiştirdiğini unutmayın. Animasyon, Durdur'u <xref:System.Windows.Media.Animation.FillBehavior>belirterek tamamlandıktan sonra animasyondan önce bulunan değere dönmek için belirtebilir. Daha sonra, temel değer belirleme için normal öncelik kullanılır.  
  
 Birden çok animasyon tek bir özelliğe uygulanabilir ve bu animasyonların her biri değer önceliğinde farklı noktalardan tanımlanmış olabilir. Ancak, bu animasyonlar, animasyonu yalnızca daha yüksek öncelikten uygulamak yerine, değerlerini biraraya getirecektir. Bu, animasyonların tam olarak nasıl tanımlandığına ve animasyonlanan değerin türüne bağlıdır. Animasyon özellikleri hakkında daha fazla bilgi için [Animasyona Genel Bakış'a](../graphics-multimedia/animation-overview.md)bakın.  
  
 Zorlama tüm en yüksek düzeyde geçerlidir. Zaten çalışan bir animasyon bile değer zorlamasına tabidir. Yerleşik zorlamadaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bazı varolan bağımlılık özellikleri vardır. Özel bağımlılık özelliği için, özel bağımlılık özelliği için zorlama davranışını, özelliği <xref:System.Windows.CoerceValueCallback> oluştururken meta verilerin bir parçası olarak geri arama yı yazıp geçirerek tanımlarsınız. Türemiş bir sınıfta ki meta verileri geçersiz kılarak varolan özelliklerin zorlama davranışını da geçersiz kılabilir. Zorlama, temel değerle, zorlama üzerindeki kısıtlamaların o anda bu kısıtlamalar mevcut olduğu gibi uygulanacağı, ancak temel değerin hala korunacağı şekilde etkileşime girilir. Bu nedenle, zorlama kısıtlamaları daha sonra kaldırılırsa, zorlama bu temel değere mümkün olan en yakın değeri döndürecek ve potansiyel olarak bir özellik üzerindeki zorlama etkisi tüm kısıtlamalar kaldırılır kaldırılmaz sona erer. Zorlama davranışı hakkında daha fazla bilgi için Bağımlılık [Özelliği Geri Aramaları ve Doğrulama'ya](dependency-property-callbacks-and-validation.md)bakın.  
  
<a name="triggers"></a>
## <a name="trigger-behaviors"></a>Tetikleyici Davranışlar  
 Denetimler genellikle temalarda varsayılan stilin bir parçası olarak tetikleyici davranışları tanımlar. Denetimler üzerinde yerel özellikleri ayarlamak, tetikleyicilerin kullanıcı tarafından yönlendirilen olaylara görsel veya davranışsal olarak yanıt verebilmelerini engelleyebilir. Bir özellik tetikleyicisinin en yaygın kullanımı denetim veya <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Örneğin, varsayılan olarak, <xref:System.Windows.Controls.Button> bir devre <xref:System.Windows.UIElement.IsEnabled%2A> dışı `false`bırakıldığında <xref:System.Windows.Controls.Control.Foreground%2A> (tetikleyici' dir) sonra tema stilindeki değer denetimin "gri leştirilmiş" görünmesine neden olur. Ancak yerel <xref:System.Windows.Controls.Control.Foreground%2A> bir değer belirlediyseniz, bu normal gri çıkış rengi, bu özellik tetiklenen senaryoda bile yerel özellik kümeniz tarafından öncelikli olarak geçersiz kılınacaktır. Tema düzeyinde tetikleyici davranışlara sahip özellikler için değerleri ayarlama konusunda dikkatli olun ve bu denetim için amaçlanan kullanıcı deneyimini gereksiz yere müdahale etmediğinizden emin olun.  
  
<a name="clearvalue"></a>
## <a name="clearvalue-and-value-precedence"></a>ClearValue ve Değer Önceliği  
 Yöntem, <xref:System.Windows.DependencyObject.ClearValue%2A> bir öğe üzerinde ayarlanmış bir bağımlılık özelliğinden yerel olarak uygulanan herhangi bir değeri temizlemek için uygun bir araç sağlar. Ancak, <xref:System.Windows.DependencyObject.ClearValue%2A> arama, özellik kaydı sırasında meta verilerde belirlenen varsayılan değerin yeni etkin değer olduğunun garantisi değildir. Değer önceliğindeki diğer katılımcıların tümü hala etkindir. Yalnızca yerel olarak ayarlanmış değer öncelik dizisinden kaldırıldı. Örneğin, bu özelliğin de bir tema stili tarafından ayarlandığı bir özelliği çağırırsanız, <xref:System.Windows.DependencyObject.ClearValue%2A> tema değeri meta veri tabanlı varsayılan yerine yeni değer olarak uygulanır. Tüm özellik değeri katılımcılarını işlemin dışına çıkarmak ve değeri kayıtlı meta veri varsayılanına ayarlamak istiyorsanız, bağımlılık özelliği meta verilerini sorgulayarak bu varsayılan değeri kesin olarak elde edebilir ve <xref:System.Windows.DependencyObject.SetValue%2A>ardından varsayılan değeri kullanarak özelliği bir çağrıyla yerel olarak ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliği Geri Aramaları ve Doğrulama](dependency-property-callbacks-and-validation.md)
