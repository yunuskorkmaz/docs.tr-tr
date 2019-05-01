---
title: Bağımlılık Özelliği Değer Önceliği
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 9adcd19ea48d62f4fdcab3380252ae8ec8398296
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010546"
---
# <a name="dependency-property-value-precedence"></a>Bağımlılık Özelliği Değer Önceliği
<a name="introduction"></a> Bu konu açıklar nasıl işleyişini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi bir bağımlılık özelliğinin değeri etkileyebilir ve hangi yönlerini özelliği tarafından sistemi geçerli etkili bir özelliğinin değerini için öncelik açıklar.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, üzerinde bir tüketici mevcut bağımlılık özellikleri perspektifinden bağımlılık özellikleri anladığınızı varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md). Bu konudaki örnekleri izlemek için de anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>WPF özellik sistemi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellik sistemi sunan bağımlılık özellikleri değeri sağlamak için güçlü bir yol tarafından çeşitli Etkenler, gerçek zamanlı özellik doğrulamasını geç bağlama ve değerleri yapılan değişikliklerin ilgili özellikleri bildirme gibi özellikleri etkinleştirmek belirlenemedi diğer özellikler için. Bağımlılık özelliği değerleri belirlemek için kullanılan mantıksal ve aynı sırada makul karmaşık. Bu sırada, gereksiz özellik ayarı önlemenize yardımcı olur ve ayrıca karışıklık ' kurmak Temizle bilmek tam olarak neden bazı etkilemek veya bir bağımlılık özelliği değer tahmin denemesi, beklenen değer kaynaklanan yukarı sona.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Bağımlılık özellikleri "birden fazla yerde ayarlanabilir"  
 Örneği verilmiştir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] burada aynı özelliğe (<xref:System.Windows.Controls.Control.Background%2A>) üç farklı "değeri etkileyebilir operations ayarladı".  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Burada, hangi rengin geçerli beklediğiniz — kırmızı, yeşil ve mavi?  
  
 Animasyonlu değerleri ve zorlama dışında yerel özellik kümeleri en yüksek öncelik ayarlanır. Yerel olarak bir değer ayarlarsanız değeri, hatta tüm stilleri veya denetim şablonları kabul edilir olduğunu bekleyebilirsiniz. Burada örnekte <xref:System.Windows.Controls.Control.Background%2A> kırmızı yerel olarak ayarlayın. Bu nedenle, aksi takdirde bu kapsamda bu türdeki tüm öğelere uygulanacak bir örtük stil olsa bile bu kapsamda tanımlanan stil verme en yüksek önceliğe değil <xref:System.Windows.Controls.Control.Background%2A> özellik değeri.  Bu düğme örneğinden yerel değer kırmızı kaldırılırsa, ardından stili önceliğe sahip ve düğmenin stili Background değerini elde edebilirsiniz.  Düğme Aksi takdirde üzerine fare ise mavi ve yeşil olur stil tetikleyiciler, önceliklidir.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Bağımlılık özelliği ayarı önceliği listesi  
 Bağımlılık özellikleri çalışma zamanı değerlerini atarken özellik sistemi kullanan kesin sırasını verilmiştir. En yüksek önceliğe önce listelenir. Bazı yapılan Genelleştirme bu listeyi genişler [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
1. **Özellik sistemi zorlama.** Zorlama hakkında ayrıntılı bilgi için bkz. [zorlama, animasyon ve temel değer](#animations) bu konuda.  
  
2. **Etkin animasyonlar veya animasyonları tutma davranış.** Bu değer yerel olarak ayarlanmış olsa bile pratik etkili sahip olmak için bir özelliğin animasyon temel (unanimated) değer üzerinde önceliğe sahip mümkün olması gerekir. Ayrıntılar için bkz [zorlama, animasyon ve temel değer](#animations) bu konuda.  
  
3. **Yerel değer.** Yerel değer özniteliği veya özelliği bir öğe olarak ayarı da karşılık gelir "sarmalayıcı" özelliği kolaylık aracılığıyla ayarlanabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veya bir çağrı tarafından <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] belirli bir örneğine bir özelliğini kullanarak. Bir bağlama veya kaynak kullanarak yerel bir değer ayarlarsanız, doğrudan bir değer olarak ayarlandıysa bu her önceliği işlevi görür.  
  
4. **TemplatedParent şablonu özellikleri.** Bir öğeye sahip bir <xref:System.Windows.FrameworkElement.TemplatedParent%2A> bir şablonunun bir parçası oluşturulmuş olsa bile (bir <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.DataTemplate>). Bu geçerli olduğunda hakkında daha fazla bilgi için bkz [TemplatedParent](#templatedparent) bu konuda. Şablon içerisinde, aşağıdaki öncelik geçerlidir:  
  
    1. Gelen tetikler <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu.  
  
    2. Özellik kümeleri (genellikle ile [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikler) içinde <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu.  
  
5. **Örtük stil.** Yalnızca geçerli `Style` özelliği. `Style` Özelliği herhangi bir stil kaynağı tarafından o öğenin türüyle eşleşen bir anahtar ile doldurulur. Stil kaynağı sayfası veya uygulama olması gerekir. Temalar bir örtük stil kaynağı için arama devam etmez.  
  
6. **Stil tetiklenir.** Sayfasından veya uygulama stilleri içindeki Tetikleyiciler (açık veya örtük stil bu stiller olabilir, ancak varsayılan stillerden daha düşük önceliğe sahip).  
  
7. **Şablon tetiklenir.** Herhangi bir tetikleyici bir şablon bir stil içinde veya doğrudan uygulanan bir şablon.  
  
8. **Stil ayarlayıcı.** Değerlerini bir <xref:System.Windows.Setter> sayfasından veya uygulama stilleri içindeki.  
  
9. **Varsayılan (tema) stili.** Bu geçerli olduğunda ve tema stilleri şablonlarında tema stilleri nasıl ilişki kuracağını hakkında daha fazla bilgi için bkz: [(tema) varsayılan stillerini](#themestyles) bu konunun devamındaki. Varsayılan stil içinde aşağıdaki öncelik sırası uygular:  
  
    1. Tema stili etkin tetikler.  
  
    2. Tema stilde ayarlayıcı.  
  
10. **Devralma.** Bunlar özellikle uygulamanın tamamında her öğe üzerinde ayarlanmaması olacak şekilde birkaç bağımlılık özellikleri değerleri alt öğeleri için üst öğeden devralır. Ayrıntılar için bkz. [özellik değeri kalıtımı](property-value-inheritance.md).  
  
11. **Bağımlılık özelliği meta verisi varsayılan değeri.** Herhangi bir verilen bağımlılık özelliği, belirli özellik özelliği sistem kaydı tarafından belirlenen varsayılan bir değere sahip. Ayrıca, bir bağımlılık özelliği devralan türetilmiş sınıflar türü başına temelinde (varsayılan değer dahil), meta verileri geçersiz kılma seçeneğiniz vardır. Bkz: [bağımlılık özelliği meta verisi](dependency-property-metadata.md) daha fazla bilgi için. Devralınmış bir özellik için varsayılan değer önce devralma denetlendiğinden bir üst öğenin varsayılan değer bir alt öğesi üzerinde önceliklidir.  Sonuç olarak, devralınabilir bir özelliği herhangi bir yere ayarlanmamışsa varsayılan değer olarak belirtilen kök veya üst alt öğe varsayılan değer yerine kullanılır.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent öncelik öğesi olarak bir öğenin doğrudan standart uygulama biçimlendirme içinde bildirdiğiniz herhangi bir özellik için geçerli değildir. Varlığı uygulaması şablonu aracılığıyla içine gelen alt öğeleri bir görsel ağacı içinde TemplatedParent kavramı vardır. Özellik sistemi arandığında <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu için bir değer bu arama o öğenin oluşturduğunuz şablonu. Özellik değerleri <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu genellikle hareket alt öğede yerel bir değer olarak ayarlanmış, ancak şablonları potansiyel olarak paylaşıldığından bu daha az önceliğe yerel değer karşılaştırması yok edildiğinde. Ayrıntılar için bkz <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Stil özelliği  
 Daha önce açıklanan arama düzenini dışındaki tüm olası bağımlılık özellikleri için geçerlidir: <xref:System.Windows.FrameworkElement.Style%2A> özelliği. <xref:System.Windows.FrameworkElement.Style%2A> Özelliği benzersiz olduğundan, bunu kendi stil olamaz, 5 ila 8 öncelikli öğeleri geçerli olmadığı için. Ayrıca animasyon ekleme veya zorlama <xref:System.Windows.FrameworkElement.Style%2A> kullanılmaması önerilir (ve animasyon <xref:System.Windows.FrameworkElement.Style%2A> özel animasyon sınıfı gerektirir). Bu, üç şekilde bırakır <xref:System.Windows.FrameworkElement.Style%2A> özelliği ayarlanmış olması:  
  
- **Açık stili.** <xref:System.Windows.FrameworkElement.Style%2A> Özelliği doğrudan ayarlayın. Çoğu senaryoda stili satır içi olarak tanımlanan değildir, ancak bunun yerine bir kaynak olarak açık anahtar tarafından başvuruluyor. Bu durumda, yerel bir değer, öncelik madde 3'ymiş gibi Style özelliği işlevi görür.  
  
- **Örtük stil.** <xref:System.Windows.FrameworkElement.Style%2A> Özelliği doğrudan ayarlanmadı. Ancak, <xref:System.Windows.FrameworkElement.Style%2A> düzeyde kaynak arama sırası (sayfası, uygulama) varsa ve stili, uygulanacak türüyle eşleşen bir kaynak anahtarı kullanılarak Anahtarlanan. Bu durumda, <xref:System.Windows.FrameworkElement.Style%2A> özelliğinin kendisini davranır dizideki öğe 5 olarak tanımlanmış bir önceliğe göre. Bu durum kullanarak algılanabilir <xref:System.Windows.DependencyPropertyHelper> karşı <xref:System.Windows.FrameworkElement.Style%2A> özelliği ve örnek kod <xref:System.Windows.BaseValueSource.ImplicitStyleReference> sonuçları.  
  
- **Varsayılan Stil**olarak da bilinen **tema stili.** <xref:System.Windows.FrameworkElement.Style%2A> Özelliği doğrudan ayarlı değil ve aslında olarak okuyacaksa `null` gönderinizi çalıştırma. Bu durumda, stili parçası olan çalışma zamanı teması değerlendirmesinden gelen gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunu altyapısı.  
  
 İçin örtük stiller Temalar içinde değil, tam olarak - türüyle eşleşmelidir bir `MyButton` `Button`-türetilmiş sınıf için bir stil örtük olarak kullanmaz `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Varsayılan (tema) stilleri  
 İle birlikte gelen her denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir varsayılan stilde. Varsayılan stili bu varsayılan stili olası nedeni tema tarafından değişir bazen bir tema stil olarak adlandırılır.  
  
 Tema stilde ayarlayıcı için olarak var olan denetim şablonunu bir denetim için varsayılan stil içinde bulunan en önemli bilgileri kendi <xref:System.Windows.Controls.Control.Template%2A> özelliği. Bir denetimi özel bir stil bir parçası olarak özel bir şablon olmadan hiçbir varsayılan stillerini şablondan varsa, hiçbir görsel görünümünü hiç gerekir. Varsayılan Stil şablondan basit bir yapı her bir denetimin görünümünü sağlar ve ayrıca şablon ve karşılık gelen denetim sınıf görsel ağacını içinde tanımlanan özellikler arasındaki bağlantıları tanımlar. Her denetim şablonu tamamen değiştirmeden denetimin görsel görünümünü etkileyebilir özellik kümesi sunar. Örneğin, varsayılan görünümünü düşünün bir <xref:System.Windows.Controls.Primitives.Thumb> bir bileşen olan denetimi, bir <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> özelleştirilebilir belirli özelliklere sahiptir. Varsayılan şablonunu bir <xref:System.Windows.Controls.Primitives.Thumb> basit bir yapı oluşturur / birkaç ile görsel ağaç'iç içe geçmiş <xref:System.Windows.Controls.Border> Eğimli görünüm oluşturmak için bileşenleri. Eğer şablonunun bir parçası olan bir özellik için özelleştirme tarafından kullanıma sunulan <xref:System.Windows.Controls.Primitives.Thumb> sınıfı bu özellik tarafından sunulmalıdır sonra bir [TemplateBinding](templatebinding-markup-extension.md), şablonu içinde. Durumunda, <xref:System.Windows.Controls.Primitives.Thumb>, çeşitli özelliklerini bu Kenarlıklar özellikleri için bir şablon bağlama gibi paylaşmak <xref:System.Windows.Controls.Border.Background%2A> veya <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ancak diğer belirli özellikler veya görsel düzenleme denetimi şablona sabit kodlanmış veya doğrudan tema gelir ve tüm şablonunu değiştirerek eksikliği değiştirilemez değerlere bağlı. Bir özellik şablonlu bir üst öğeden gelen ve şablon bağlama tarafından sunulmadığından, hedeflemek için kolay bir yolu olmadığından genel olarak, bu stilleri tarafından ayarlanamaz. Ancak bu özellik hala özellik değeri devralma uygulanan şablonunda veya varsayılan değer etkisinde.  
  
 Tema stilleri bir tür tanımlarını anahtarı olarak kullanın. Temalar verilen öğe örneğine uygulandığında, ancak bu tür için Temalar arama denetleyerek gerçekleştirilir <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> denetim özelliği. Örtük stilleri gibi değişmez değer türü kullanarak aksine budur. Değerini <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> bile bunu (özelliğini değiştirme hedeflenen yoludur, özellik düzeyinde ancak için bunun yerine varsayılan değer özelliği meta verilerinde değişiklik kılmamak) uygulayan değiştirmedi türetilmiş sınıflara devralır. Tema stilleri için stil olmayan türetilmiş öğeler tanımlamak temel sınıflar bu yöneltme sağlar (veya daha da önemlisi, o stilin içinde bir şablonunuzun olmadığı ve dolayısıyla varsayılan görünümünü hiç gerekir). Bu nedenle, türetebilirsiniz `MyButton` gelen <xref:System.Windows.Controls.Button> ve yine de alırsınız <xref:System.Windows.Controls.Button> varsayılan şablonu. Denetim yazarı olsaydı `MyButton` ve farklı bir davranış istiyordu, bağımlılık özelliği meta verileri geçersiz kılma <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> üzerinde `MyButton` farklı bir anahtar dönün ve ardından şablon dahil olmak üzere ilgili tema stilleri tanımlayın için `MyButton` ile paketin, `MyButton` denetimi. Temalar, stillerini ve denetim yazma hakkında daha fazla bilgi için bkz. [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dinamik kaynak başvurularını ve bağlama  
 Dinamik kaynak başvurularını ve bağlama işlemleri başlangıçtan ayarlanırlar konumu önceliğini uyar. Örneğin, yerel bir değere uygulanan bir dinamik kaynak öncelik 3 Öğe başına çalışır, öncelik öğesi 9 ve benzeri bir bağlama için bir özellik ayarlayıcısı tema stil içinde geçerlidir. Olduğundan dinamik kaynak başvurularını ve bağlama hem sağlayabilmelidir uygulamanın çalışma zamanı durumu değerlerini almak, bu çalışma zamanına verilen bir özellik için özelliği değer önceliği belirleme gerçek işlemi genişleten kapsar.  
  
 Dinamik kaynak başvurularını NET olarak söylemek gerekirse özellik sistemi parçası değildir, ancak kendi, yukarıda listelenen dizisi etkileşimde bir arama sırası sahiptirler. Bu öncelik daha kapsamlı olarak belgelenmiştir [XAML kaynakları](xaml-resources.md). Temel özetleme, önceliği olan: sayfa kök, uygulama, tema, sistem öğesi.  
  
 Dinamik kaynakları ve bağlantıları burada ayarlanan, önceliğe sahiptir, ancak değeri ertelendi. Bunun bir sonucu bir dinamik kaynak ya da yerel değere bağlama, yerel değeri için herhangi bir değişiklik dinamik kaynak veya tamamen bağlama yerine olmasıdır. Çağırsanız bile <xref:System.Windows.DependencyObject.ClearValue%2A> yöntemi yerel olarak ayarlanmış temizlemek için değer, dinamik kaynak ya da bağlama değil geri yüklenir. Aslında, çağırırsanız <xref:System.Windows.DependencyObject.ClearValue%2A> (değişmez değer yerel değer yok ile) yerinde dinamik kaynak ya da bağlama sahip bir özellik, bunlar tarafından temizlenir <xref:System.Windows.DependencyObject.ClearValue%2A> çok çağırın.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Yöntemi, bir özelliği ayarlamak başka bir yoludur, ancak öncelik sırasına göre değil. Bunun yerine, <xref:System.Windows.DependencyObject.SetCurrentValue%2A> bir özelliğin değerini kaynak önceki değerin üzerine yazmadan değiştirmenize olanak tanır. Kullanabileceğiniz <xref:System.Windows.DependencyObject.SetCurrentValue%2A> yerel bir değerin öncelik değeri vermeden bir değer ayarlamak istiyorsanız dilediğiniz zaman. Örneğin bir özellik tetikleyicisi tarafından belirlenir ve ardından başka bir değer aracılığıyla atanan <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, özellik sistemi hala tetikleyici uyar ve tetikleyici eylem oluşursa özellik değişecektir. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> özelliğin değeri, daha yüksek bir önceliğe sahip bir kaynak vermeden değiştirmenize olanak tanır. Benzer şekilde, kullanabileceğiniz <xref:System.Windows.DependencyObject.SetCurrentValue%2A> bağlama yazmadan bir özelliğin değerini değiştirmek için.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Zorlama, animasyonları ve taban değeri  
 Her ikisi de bu "taban değeri" olarak ifade edilen bir değer üzerinde işlem yapacağı zorlama ve animasyon [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Temel böylece ne olursa olsun değer 2 öğesi ulaşılana kadar yukarı öğeleri değerlendirme aracılığıyla belirlenir değerdir.  
  
 Animasyon için taban değeri animasyonun, "Kimden" ve "İçin" belirli davranışları belirtmiyor veya animasyonun kasıtlı olarak tamamlandığında temel değere döner animasyonlu değer üzerinde bir etkisi olabilir. Bu uygulamada görmek için şunu çalıştırın [gelen, için ve animasyon hedef değerleri örnek tarafından](https://go.microsoft.com/fwlink/?LinkID=159988). Tüm "Kimden" animasyondaki ilk yerel değer farklıdır, örnekte dikdörtgenin yüksekliğini yerel değerlerini ayarlamayı deneyin. Animasyonları "Kimden" değerlerini hemen kullanmaya başlayın ve başlatıldığında temel değerin yerini fark edeceksiniz. Animasyon Durdur belirterek tamamlandıktan sonra animasyon önce bulunan değeri döndürülecek belirtebilir <xref:System.Windows.Media.Animation.FillBehavior>. Ardından, normal öncelik temel değerin belirlenmesi için kullanılır.  
  
 Birden çok animasyon, her biri farklı noktalarından değer önceliği büyük olasılıkla tanımlanmış animasyonlarına ile tek bir özellik için uygulanabilir. Ancak, büyük olasılıkla animasyonlarına olur bileşik yalnızca daha yüksek önceliği animasyon uygulamak yerine bunların değerleri. Bu, animasyonları tam olarak nasıl tanımlandığını ve animasyon uygulanan değerin türü bağlıdır. Özellikleri hakkında daha fazla bilgi için bkz. [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
 Zorlama tüm en üst düzeyde uygulanır. Zaten çalışan bir animasyon değeri işlemine tabi olur. Belirli mevcut bağımlılık özelliklerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleşik zorlama sahip. Özel bağımlılık özelliği için özel bir bağımlılık özelliği için zorlama davranışı yazarak tanımladığınız bir <xref:System.Windows.CoerceValueCallback> ve özelliği oluşturduğunuzda meta verilerinin bir parçası geri çağırma geçirme. Ayrıca bu özellik, türetilen bir sınıfta meta verileri geçersiz kılarak mevcut özelliklerin zorlama davranışı geçersiz kılabilirsiniz. Temel değerin zorlama kısıtlamalar uygulanır şekilde etkileşim zorlama zaman kısıtlamalar var, ancak temel değer yine de korunur. Bu nedenle, zorlama kısıtlamalarını sonraki yükseltilmiş, zorlama en yakın değere olası bu taban değeri döndürür ve tüm kısıtlamalar yükseltilmiş hemen sonra bir özellik üzerinde zorlama etkisi sona erecek. Zorlama davranış hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri aramaları ve doğrulama](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Tetikleyici davranışları  
 Denetimleri, temalar, varsayılan stilde bir parçası olarak genellikle tetikleyici davranışları tanımlar. Yerel özellikleri denetimlerinde ayarlama Tetikleyiciler görsel olarak veya davranışsal kullanıcı temelli olaylara yanıt vermesi mümkün olmasını engelleyebilir. Bir özellik tetikleyicisi en yaygın kullanımı denetimi veya durumu özellikleri olduğu gibi <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Örneğin, varsayılan olarak, bir <xref:System.Windows.Controls.Button> devre dışı bırakıldı (tetiklemek için <xref:System.Windows.UIElement.IsEnabled%2A> olduğu `false`) sonra <xref:System.Windows.Controls.Control.Foreground%2A> tema stili değer "gri renkte" görüntülenmesinin denetimini ne neden olur. Ancak yerel bir ayarlarsanız <xref:System.Windows.Controls.Control.Foreground%2A> değeri normal çıkış gri renk önceliği bile bu senaryoda özelliği ile tetiklenen, yerel özellik kümesi tarafından kılınır. Tema düzeyinde tetikleyici davranışları, unduly bu denetim için hedeflenen bir kullanıcı deneyimiyle engel olduğundan emin olun ve özellikleri için değer ayarını dikkatli olun.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue ve değer önceliği  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Yöntemi bir expedient anlamına gelir yerel olarak uygulanan herhangi bir öğede ayarlanan bir bağımlılık özelliği değerini temizlemek sağlar. Ancak, çağırma <xref:System.Windows.DependencyObject.ClearValue%2A> meta verilerinde özelliği kayıt sırasında belirlenen varsayılan yeni geçerli değerini olduğuna dair bir garanti değildir. Hala etkin olan tüm diğer katılımcıları değer önceliği. Yalnızca yerel olarak ayarlanan değer öncelik dizisinden kaldırıldı. Örneğin, eğer <xref:System.Windows.DependencyObject.ClearValue%2A> özellikte burada bu özellik ayrıca bir tema stili tarafından ayarlanır ve ardından değeri meta verileri alarak varsayılan yerine yeni bir değer olarak uygulanır. İşlemin dışında tüm özellik değeri katılımcıları alabilir ve kayıtlı meta verileri varsayılan değer ayarlamak istiyorsanız, bağımlılık özelliği meta verisi ve ardından sorgulama tarafından kesin bir şekilde varsayılan değeri varsayılan değere yerel olarak kullanabileceğiniz edinebilirsiniz özelliğini çağrısıyla <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Bağımlılık Özelliği Geri Aramaları ve Doğrulama](dependency-property-callbacks-and-validation.md)
