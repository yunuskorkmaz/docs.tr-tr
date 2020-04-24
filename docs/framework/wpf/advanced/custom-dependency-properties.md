---
title: Özel Bağımlılık Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: e4117d7add2a34d6d989d9222e7688361cf6b379
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646350"
---
# <a name="custom-dependency-properties"></a>Özel Bağımlılık Özellikleri

Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama geliştiricilerin inanın özel bağımlılık özelliği oluşturmak isteyebileceği nedenleri açıklar ve uygulama adımlarının yanı sıra özelliğin performansını, kullanılabilirliğini veya çok yönlülüğünü artırabilecek bazı uygulama seçeneklerini açıklar.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Ön koşullar

Bu konu, bağımlılık özelliklerini sınıflardaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varolan bağımlılık özelliklerinin tüketici perspektifinden anladığınızı ve Bağımlılık Özelliklerine Genel [Bakış](dependency-properties-overview.md) konusunu okuduğunuzu varsayar. Bu konudaki örnekleri takip etmek için, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamaların nasıl yazAcağını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] da anlamalı ve bilmelidir.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Bağımlılık Özelliği Nedir?

Bir bağımlılık özelliği olarak uygulayarak stil, veri bağlama, devralma, animasyonlar ve varsayılan değerleri desteklemek için ortak bir dil çalışma zamanı (CLR) özelliği olacağını etkinleştirebilirsiniz. Bağımlılık [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, <xref:System.Windows.DependencyProperty.Register%2A> yöntem (veya) <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>çağırılarak özellik sistemine kayıtlı olan ve tanımlayıcı <xref:System.Windows.DependencyProperty> alanı tarafından desteklenen özelliklerdir. Bağımlılık özellikleri yalnızca türlere <xref:System.Windows.DependencyObject> göre <xref:System.Windows.DependencyObject> kullanılabilir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf hiyerarşisinde oldukça yüksektir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu nedenle kullanılabilir sınıfların çoğunluğu bağımlılık özelliklerini destekleyebilir. Bağımlılık özellikleri ve bu SDK'da bunları açıklamak için kullanılan bazı terminoloji ve sözleşmeler hakkında daha fazla bilgi [için](dependency-properties-overview.md)bkz.

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Bağımlılık Özellikleri Örnekleri

Sınıflarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanan bağımlılık özelliklerine örnek olarak, <xref:System.Windows.Controls.Control.Background%2A> diğerleri <xref:System.Windows.FrameworkElement.Width%2A> arasında özellik, <xref:System.Windows.Controls.TextBox.Text%2A> özellik ve özellik verilebilir. Bir sınıf tarafından maruz kalan her bağımlılık özelliği, <xref:System.Windows.DependencyProperty> aynı sınıfta açıkta olan karşılık gelen ortak statik bir tür alanına sahiptir. Bu bağımlılık özelliği için tanımlayıcıdır. Tanımlayıcı bir kural kuralı kullanılarak adlandırılır: bağlılık özelliğinin adı, `Property` dize ile ona eklenir. Örneğin, <xref:System.Windows.DependencyProperty> <xref:System.Windows.Controls.Control.Background%2A> özellik için karşılık gelen tanımlayıcı alanı <xref:System.Windows.Controls.Control.BackgroundProperty>. Tanımlayıcı, bağımlılık özelliği hakkındaki bilgileri kaydedilirken depolar ve tanımlayıcı daha sonra bağımlılık özelliğini içeren diğer işlemler için kullanılır. <xref:System.Windows.DependencyObject.SetValue%2A>

[Bağımlılık Özellikleri Genel Bakış](dependency-properties-overview.md)belirtildiği gibi, tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri (en bağlı özellikleri hariç) da CLR özellikleri nedeniyle "sarmalayıcı" uygulaması vardır. Bu nedenle, koddan, sarmalayıcıları tanımlayan CLR erişimcileri çağırarak bağımlılık özelliklerini diğer CLR özelliklerini kullandığınız şekilde alabilirsiniz veya ayarlayabilirsiniz. Yerleşik bağımlılık özelliklerinin bir tüketicisi olarak, genellikle <xref:System.Windows.DependencyObject> <xref:System.Windows.DependencyObject.GetValue%2A> temel <xref:System.Windows.DependencyObject.SetValue%2A>özellik sistemine bağlantı noktası olan yöntemleri ve (temel özellik sistemi) kullanmayın. Bunun yerine, CLR özelliklerinin varolan uygulaması, `get` tanımlayıcı `set` alanını uygun şekilde kullanarak özelliğin ve sarıcı uygulamalarının içinde ve <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> önceden çağrılmış olacaktır. Özel bağımlılık özelliğini kendiniz uyguluyorsanız, sarıcıyı da benzer bir şekilde tanımlıyor olabilirsiniz.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Bağımlılık Özelliğine Ne Zaman Uygulamanız Gerekir?

Bir özellik bir sınıfüzerinde uyguladığınızda, sınıfınız türetilmiştir <xref:System.Windows.DependencyObject>sürece, bir tanımlayıcı ile <xref:System.Windows.DependencyProperty> mülkiyet inizi yedekleme ve böylece bir bağımlılık özelliği yapmak için seçeneğiniz vardır. Mülkünüzün bir bağımlılık özelliği olması her zaman gerekli veya uygun değildir ve senaryo gereksinimlerinize bağlıdır. Bazen, özel bir alan ile mülkiyet destek tipik tekniği yeterlidir. Ancak, özelliğinizin aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerden birini veya daha fazlasını desteklemesini istediğinizde, mülkünüzü bağımlılık özelliği olarak uygulamanız gerekir:

- Mülkünüzün bir tarzda ayarlanabilmesini istiyorsunuz. Daha fazla bilgi için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.

- Mülkünüzün veri bağlamayı desteklemesini istiyorsunuz. Veri bağlama bağımlılık özellikleri hakkında daha fazla bilgi için [bkz.](../data/how-to-bind-the-properties-of-two-controls.md)

- Mülkünüzün dinamik bir kaynak başvurusuyla ayarlanabilmesini istiyorsunuz. Daha fazla bilgi için [Bkz. XAML Kaynakları.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)

- Öğe ağacındaki bir üst öğeden otomatik olarak bir özellik değeri devralmak istiyorsunuz. Bu durumda, CLR <xref:System.Windows.DependencyProperty.RegisterAttached%2A> erişimi için bir özellik sarıcı oluştursanız bile yönteme kaydolun. Daha fazla bilgi için [Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)

- Mülkünüzün animatable olmasını istiyorsunuz. Daha fazla bilgi için [Animasyona Genel Bakış'a](../graphics-multimedia/animation-overview.md)bakın.

- Özellik sisteminin, özellik sistemi, çevre veya kullanıcı tarafından gerçekleştirilen eylemlerle veya stilleri okuyup kullanarak, özelliğin önceki değerinin değiştirildiğinde rapor etmesini istiyorsunuz. Özellik meta verilerini kullanarak, özellik sisteminiz mülk sisteminizin kesin olarak değiştirildiğini her belirlediğinde çağrılacak bir geri arama yöntemi belirtebilirsiniz. İlgili bir kavram özellik değeri zorlamadır. Daha fazla bilgi için Bkz. [Bağımlılık Özelliği Geri Aramaları ve Doğrulama.](dependency-property-callbacks-and-validation.md)

- Bir özellik değerini değiştirmenin bir öğe için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görselleri yeniden oluşturmak için düzen sisteminin gerekli olup olmadığını bildirmek gibi işlemler tarafından da kullanılan yerleşik meta veri kuralları kullanmak istiyorsunuz. Veya türetilen sınıfların varsayılan değer gibi meta veri tabanlı özellikleri değiştirebilmesi için meta veri geçersiz kılmalarını kullanabilmek istiyorsunuz.

- **Özellikler** pencere düzenlemesi gibi Visual Studio WPF Designer desteğini almak için özel denetim özellikleri istiyorsunuz. Daha fazla bilgi için [bkz.](../controls/control-authoring-overview.md)

Bu senaryoları incelediğinizde, tamamen yeni bir özellik uygulamak yerine varolan bir bağımlılık özelliğinin meta verilerini geçersiz kılarak senaryonuzu elde edip edemeyeceğiniz de göz önünde bulundurulmalıdır. Meta veri geçersiz kılmanın pratik olup olmadığı senaryonuza ve bu senaryonun [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varolan bağımlılık özellikleri ve sınıflarında uygulamaya ne kadar benzediğine bağlıdır. Varolan özelliklerdeki meta verilerin geçersiz kılınması hakkında daha fazla bilgi için Bkz. [Bağımlılık Özelliği Meta verileri.](dependency-property-metadata.md)

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Bağımlılık Özelliği Tanımlama Denetim Listesi

Bağımlılık özelliğini tanımlamak dört farklı kavramdan oluşur. Bu kavramlar mutlaka katı yordam adımları değildir, çünkü bunlardan bazıları uygulamada tek kod satırı olarak birleştirildiğinden:

- (İsteğe bağlı) Bağımlılık özelliği için özellik meta verileri oluşturun.

- Mülk türünü ve özellik değerinin türünü belirterek özellik adını özellik sistemine kaydedin. Ayrıca, kullanılırsa özellik meta verilerini de belirtin.

- Bir <xref:System.Windows.DependencyProperty> tanımlayıcıyı sahip türünde `public` `static` `readonly` bir alan olarak tanımlayın.

- Adı bağımlılık özelliğinin adıyla eşleşen bir CLR "sarmalayıcı" özelliği tanımlayın. CLR "sarmalayıcı" özelliğini `get` ve `set` erişimini, onu destekleyen bağımlılık özelliğiyle bağlantı kurmak için uygulayın.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Mülkiyet Sistemi ile Mülkiyet Kayıt

Özelliğinizin bir bağımlılık özelliği olabilmesi için, bu özelliği özellik sistemi tarafından korunan bir tabloya kaydetmeniz ve daha sonraki özellik sistemi işlemleri için niteleyici olarak kullanılan benzersiz bir tanımlayıcı vermeniz gerekir. Bu işlemler dahili işlemler veya özellik sistemi API'lerini çağıran kendi kodunuz olabilir. Özelliği kaydetmek için, <xref:System.Windows.DependencyProperty.Register%2A> yöntemi sınıfınızın gövdesi içinde (sınıfın içinde, ancak herhangi bir üye tanımı dışında) çağırırsınız. Tanımlayıcı alanı da <xref:System.Windows.DependencyProperty.Register%2A> yöntem çağrısı tarafından, return value olarak sağlanır. Aramanın diğer <xref:System.Windows.DependencyProperty.Register%2A> üye tanımları dışında yapılmasının nedeni, bu iade değerini sınıfınızın `public` `static` `readonly` bir <xref:System.Windows.DependencyProperty> parçası olarak bir tür alanı atamak ve oluşturmak için kullanmanızdır. Bu alan, bağımlılık özelliğinizin tanımlayıcısı olur.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Bağımlılık Özellik Adı Kuralları

İstisnai durumlar hariç tüm durumlarda izlemeniz gereken bağımlılık özellikleriyle ilgili yerleşik adlandırma kuralları vardır.

Bağımlılık özelliğinin kendisi temel bir ada sahip olacak, "AquariumGraphic" bu örnekte <xref:System.Windows.DependencyProperty.Register%2A>olduğu gibi, hangi ilk parametre olarak verilir . Bu ad, her kayıt türü içinde benzersiz olmalıdır. Temel türler üzerinden devralınan bağımlılık özellikleri zaten kayıt türünün bir parçası olarak kabul edilir; devralınan mülklerin adları yeniden kaydedilemez. Ancak, bu bağımlılık özelliği devralınmasa bile bir sınıfın bağımlılık özelliğinin sahibi olarak sınıf ekleme tekniği vardır; ayrıntılar için [Bkz. Bağımlılık Özelliği Meta verileri.](dependency-property-metadata.md)

Tanımlayıcı alanını oluşturduğunuzda, bu alanı, kaydettiğiniz özelliğin adıyla ve sonek 'e `Property`göre adlandırın. Bu alan bağımlılık özelliği için tanımlayıcıdır ve daha sonra, kendi kodunuzla, <xref:System.Windows.DependencyObject.SetValue%2A> izin <xref:System.Windows.DependencyObject.GetValue%2A> verdiğiniz herhangi bir harici kod erişimi, özellik sistemi tarafından ve potansiyel olarak işlemciler tarafından, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kendi kodunuztarafından özelliğe başka bir kod erişimi tarafından, sarmalayıcılar ve yaptığınız aramalar için bir giriş olarak kullanılacaktır.

> [!NOTE]
> Sınıf gövdesinde bağımlılık özelliğitanımlanması tipik bir uygulamadır, ancak sınıf statik oluşturucubir bağımlılık özelliği tanımlamak da mümkündür. Bağımlılık özelliğini başlatmayı sağlamak için birden fazla kod satırına ihtiyacınız varsa, bu yaklaşım anlamlı olabilir.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>"Sarma makinesinin" uygulanması

Sarmalayıcı uygulamauygulama <xref:System.Windows.DependencyObject.GetValue%2A> da `get` aramalıdır <xref:System.Windows.DependencyObject.SetValue%2A> ve `set` uygulamada (orijinal kayıt çağrısı ve alan burada da netlik için gösterilir).

İstisnai durumlar hariç tüm durumlarda, sarmalayıcı uygulamalarınız sırasıyla yalnızca <xref:System.Windows.DependencyObject.GetValue%2A> eylemleri gerçekleştirmelidir. <xref:System.Windows.DependencyObject.SetValue%2A> Bunun nedeni [xaml Yükleme ve Bağımlılık Özellikleri](xaml-loading-and-dependency-properties.md)konusunda ele alınmıştır.

Sınıflarda sağlanan tüm varolan genel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri bu basit sarıcı uygulama modelini kullanır; bağımlılık özelliklerinin çalışma biçiminin karmaşıklığının çoğu, özellik sisteminin doğal olarak bir davranışıdır veya özellik meta verileri aracılığıyla zorlama veya özellik değişikliği geri aramaları gibi diğer kavramlar aracılığıyla uygulanır.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Yine, sözleşmeye göre, sarıcı özelliğinin adı seçilen adla aynı olmalıdır ve <xref:System.Windows.DependencyProperty.Register%2A> özelliği kaydeden çağrının ilk parametresi olarak verilmelidir. Mülkünüz sözleşmeye uymuyorsa, bu durum tüm olası kullanımları devre dışı bırakmıyor, ancak birkaç önemli sorunla karşılaşacaksınız:

- Stillerin ve şablonların belirli yönleri çalışmaz.

- Çoğu araç ve tasarımcı, uygun şekilde seri hale [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]getirmek veya mülk başına bir düzeyde tasarımcı ortamı yardımı sağlamak için adlandırma kurallarına güvenmelidir.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Yükleyicinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geçerli uygulaması sarmalayıcıları tamamen atlar ve öznitelik değerlerini işlerken adlandırma kuralına dayanır. Daha fazla bilgi için Bkz. [XAML Yükleme ve Bağımlılık Özellikleri.](xaml-loading-and-dependency-properties.md)

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Yeni Bağımlılık Özelliği için Özellik Meta Verileri

Bir bağımlılık özelliği kaydettiğinizde, özellik sistemi üzerinden kayıt özelliği özellikleri depolar bir meta veri nesnesi oluşturur. Bu özelliklerin çoğu, özellik basit imzaları ile kayıtlı ise <xref:System.Windows.DependencyProperty.Register%2A>ayarlanan varsayılanları vardır. Diğer imzalar, özelliği kaydederken istediğiniz meta verileri belirtmenize <xref:System.Windows.DependencyProperty.Register%2A> olanak sağlar. Bağımlılık özellikleri için verilen en yaygın meta veri, onlara özelliği kullanan yeni örneklerde uygulanan varsayılan bir değer vermektir.

Türemiş bir sınıfta bulunan bir bağımlılık özelliği <xref:System.Windows.FrameworkElement>oluşturuyorsanız, taban <xref:System.Windows.FrameworkPropertyMetadata> <xref:System.Windows.PropertyMetadata> sınıf yerine daha özel leştirilmiş meta veri sınıfını kullanabilirsiniz. <xref:System.Windows.FrameworkPropertyMetadata> Sınıfın oluşturucusu, birlikte çeşitli meta veri özellikleri belirtebileceğiniz birkaç imzaya sahiptir. Yalnızca varsayılan değeri belirtmek istiyorsanız, tek bir tür <xref:System.Object>parametresi alan imzayı kullanın. Bu nesne parametresini mülkünüz için türe özgü varsayılan değer olarak geçirin (sağlanan varsayılan `propertyType` <xref:System.Windows.DependencyProperty.Register%2A> değer, çağrıda parametre olarak sağladığınız tür olmalıdır).

Bunun <xref:System.Windows.FrameworkPropertyMetadata>için, mülkünüz için meta veri seçeneği bayrakları da belirtebilirsiniz. Bu bayraklar, kayıttan sonra özellik meta verilerinde ayrı kılmış özelliklere dönüştürülür ve belirli koşullu durumları düzen altyapısı gibi diğer işlemlere iletmek için kullanılır.

#### <a name="setting-appropriate-metadata-flags"></a>Uygun Meta veri bayraklarını ayarlama

- Mülkünüz (veya değerindeki değişiklikler) [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]düzeni nizi etkiliyorsa ve özellikle düzen sisteminin bir sayfada öğenizi nasıl boyutlandırması <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>veya <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>işlemesi gerektiğini etkiliyorsa, aşağıdaki bayraklardan birini veya birkaçını ayarlayın: . .

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>bu özellik değişikliği içeren nesne üst [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde daha fazla veya daha az yer gerektirebilir işleme için bir değişiklik gerektirir gösterir. Örneğin, bir "Genişlik" özelliği bu bayrak kümesi ne olmalıdır.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>bu özellik değişikliği genellikle özel alanda [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir değişiklik gerektirmez işleme için bir değişiklik gerektirdiğini gösterir, ancak alan içinde konumlandırma değişti gösterir. Örneğin, bir "Hizalama" özelliği bu bayrak kümesine sahip olmalıdır.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>düzen ve ölçüyü etkilemeyen, ancak başka bir işleme gerektirecek başka bir değişikliğin oluştuğunu gösterir. Bir örnek, "Arka Plan" gibi varolan bir öğenin rengini değiştiren bir özellik olacaktır.

  - Bu bayraklar genellikle özellik sistemi veya düzen geri aramaları kendi geçersiz kılma uygulamaları için meta verilerde bir protokol olarak kullanılır. Örneğin, örneğin herhangi <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> bir özelliği bir <xref:System.Windows.UIElement.InvalidateArrange%2A> değer değişikliği rapor ve meta verilerinde <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> olduğu gibi `true` varsa arayacak bir geri arama olabilir.

- Bazı özellikler, yukarıda belirtilen gerekli boyuttaki değişikliklerin üstünde ve ötesinde, içeren üst öğenin oluşturma özelliklerini etkileyebilir. Bir örnek, <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> akış belgesi modelinde kullanılan ve bu özellikteki değişikliklerin paragrafı içeren akış belgesinin genel işlemesini değiştirebileceği özelliktir. Kendi <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> özelliklerinizde benzer servis taleplerini kullanın veya tanımlayın.

- Varsayılan olarak, bağımlılık özellikleri veri bağlamayı destekler. Veri bağlama için gerçekçi bir senaryo nun olmadığı veya büyük bir nesne için veri bağlama performansının sorun olarak kabul edildiği durumlarda veri bağlamayı kasıtlı olarak devre dışı kullanabilirsiniz.

- Varsayılan olarak, <xref:System.Windows.Data.Binding.Mode%2A> bağımlılık özellikleri için veri <xref:System.Windows.Data.BindingMode.OneWay>bağlama varsayılan olarak . Bağlama örneğine <xref:System.Windows.Data.BindingMode.TwoWay> göre bağlamayı her zaman değiştirebilirsiniz; ayrıntılar için [bkz.](../data/how-to-specify-the-direction-of-the-binding.md) Ancak bağımlılık özelliği yazarı olarak, özelliği varsayılan olarak <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modunu kullanmayı seçebilirsiniz. Varolan bir bağımlılık özelliğine <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>örnek olarak; bu özellik için <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> senaryo, ayar mantığı ve varsayılan <xref:System.Windows.Controls.MenuItem> tema stili ile etkileşim birleştirme olmasıdır. Özellik <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> mantığı, diğer durum özellikleri ve yöntem çağrılarına uygun olarak özelliğin durumunu korumak için yerel olarak veri bağlama kullanır. Varsayılan olarak bağlanan <xref:System.Windows.Data.BindingMode.TwoWay> bir başka <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>örnek özellik ise.

- <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> Bayrağı ayarlayarak özel bağımlılık özelliğinde özellik devralmayı da etkinleştirebilirsiniz. Özellik devralma, üst öğelerin ve alt öğelerin ortak bir özelliğe sahip olduğu bir senaryo için yararlıdır ve alt öğelerin belirli bir özellik değerinin üst öğeyi ayarladığı değerle aynı değere ayarlatMası mantıklıdır. Örnek bir devralılabilir <xref:System.Windows.FrameworkElement.DataContext%2A>özellik, veri sunumu için önemli ana ayrıntı senaryosunu etkinleştirmek için bağlama işlemleri için kullanılır. Devredilebilir <xref:System.Windows.FrameworkElement.DataContext%2A> hale getirerek, herhangi bir alt öğe de bu veri bağlamında devralmak. Özellik değeri devralma nedeniyle, sayfa veya uygulama kökünde bir veri bağlamı belirtebilirsiniz ve olası tüm alt öğelerde bağlayıcılar için yeniden belirtmeniz gerekmez. <xref:System.Windows.FrameworkElement.DataContext%2A>devralmanın varsayılan değeri geçersiz kılması gerektiğini göstermek için de iyi bir örnektir, ancak her zaman belirli bir alt öğeüzerinde yerel olarak ayarlanabilir; ayrıntılar için bkz. [Hiyerarşik Verilerle Ana Ayrıntı Deseni'ni kullanın.](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) Özellik değeri devralma olası bir performans maliyeti var ve bu nedenle tutumlu kullanılmalıdır; ayrıntılar için [Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)

- Bağımlılık <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> özelliğinizin algılanması veya gezinme günlüğü hizmetleri tarafından kullanılması gerekip gerekmediğini belirtmek için bayrağı ayarlayın. Bir örnek <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> özelliğidir; bir seçim denetiminde seçilen herhangi bir öğe günlük geçmişi gezinildiğinde kalıcı olmalıdır.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri

Salt okunur bir bağımlılık özelliği tanımlayabilirsiniz. Ancak, mülkünüzü salt okunur olarak tanımlayabilmenizin neden olduğu senaryoları, özellik sistemine kaydetme ve tanımlayıcıyı açığa çıkarma yordamı gibi biraz farklıdır. Daha fazla bilgi için [bkz.](read-only-dependency-properties.md)

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri

Koleksiyon türü bağımlılık özelliklerigöz önünde bulundurulması gereken bazı ek uygulama sorunları vardır. Ayrıntılar için [Bkz. Koleksiyon Türü Bağımlılık Özellikleri.](collection-type-dependency-properties.md)

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Bağımlılık Özelliği Güvenliği Hususlar

Bağımlılık özellikleri ortak özellikler olarak bildirilmelidir. Bağımlılık özelliği tanımlayıcı alanları ortak statik alanlar olarak bildirilmelidir. Diğer erişim düzeylerini (korumalı gibi) bildirmeye çalışsanız bile, bir bağımlılık özelliğine özellik sistemi API'leri ile birlikte tanımlayıcı üzerinden her zaman erişilebilir. Korumalı bir tanımlayıcı alanı bile, özellik sisteminin <xref:System.Windows.LocalValueEnumerator>bir parçası olan meta veri raporlaması veya değer belirleme API'leri nedeniyle potansiyel olarak erişilebilir. Daha fazla bilgi için Bkz. [Bağımlılık Özelliği Güvenliği.](dependency-property-security.md)

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Bağımlılık Özellikleri ve Sınıf Yapıcılar

Yönetilen kod programlamada (genellikle FxCop gibi kod çözümleme araçları tarafından uygulanan) sınıf oluşturucularının sanal yöntem aramaması gerektiğine dair genel bir ilke vardır. Bunun nedeni, türemiş bir sınıf oluşturucusu temel başlatma olarak adlandırılabilir ve oluşturucu aracılığıyla sanal yöntem girilmesi, oluşturulmakta olan nesne örneğinin eksik bir başlatma durumunda oluşabilir. Zaten türetilmiştir herhangi bir sınıftan <xref:System.Windows.DependencyObject>türettiğinizde, özellik sisteminin kendisi çağırır ve dahili sanal yöntemler ortaya koymaktadır farkında olmalıdır. Bu sanal yöntemler özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistemi hizmetlerinin bir parçasıdır. Yöntemleri geçersiz kılmak, türemiş sınıfların değer belirlemeye katılmasını sağlar. Çalışma zamanı başlatma ile ilgili olası sorunları önlemek için, çok özel bir oluşturucu deseni izlemediğiniz sürece, sınıfların oluşturucuları içinde bağımlılık özelliği değerlerini ayarlamamalısınız. Ayrıntılar için, [Bağımlılık Nesneleri için Güvenli Oluşturucu Desenleri'ne](safe-constructor-patterns-for-dependencyobjects.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)
- [XAML Yükleme ve Bağımlılık Özellikleri](xaml-loading-and-dependency-properties.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](safe-constructor-patterns-for-dependencyobjects.md)
