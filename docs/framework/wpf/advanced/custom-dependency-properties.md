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
ms.openlocfilehash: 1352876b79e103d20d08382ab088f7777c6fe2ae
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401572"
---
# <a name="custom-dependency-properties"></a>Özel Bağımlılık Özellikleri

Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama geliştiricilerinin ve bileşen yazarlarının özel bağımlılık özelliği oluşturmak isteyebileceğiniz nedenleri açıklar ve uygulama adımlarının yanı sıra performansı artıran bazı uygulama seçeneklerini açıklar, Özelliğin kullanılabilirliği veya çok yönlülüğü.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Önkoşullar

Bu konuda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıflarda mevcut bağımlılık özelliklerinin bir tüketicisinin perspektifinden bağımlılık özelliklerini anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md) konusunu okuduğunuzu varsaymış olursunuz. Bu konudaki örnekleri izlemek için, uygulamaların nasıl yazılacağını [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de anlamanız ve bilmeniz gerekir.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Bağımlılık özelliği nedir?

Aynı şekilde, bir bağımlılık özelliği olarak uygulayarak stil, veri bağlama, devralma, animasyonlar ve varsayılan değerleri desteklemek için ortak dil çalışma zamanı (CLR) özelliğinin ne olduğunu seçebilirsiniz. Bağımlılık özellikleri, <xref:System.Windows.DependencyProperty.Register%2A> yöntemi çağırarak (veya <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>) ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir <xref:System.Windows.DependencyProperty> tanımlayıcı alan tarafından desteklenen özellik sistemiyle kaydedilen özelliklerdir. Bağımlılık <xref:System.Windows.DependencyObject> özellikleri yalnızca türler tarafından kullanılabilir, ancak <xref:System.Windows.DependencyObject> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf hiyerarşisinde oldukça yüksek olduğundan, ' de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bulunan sınıfların çoğu bağımlılık özelliklerini destekleyebilir. Bağımlılık özellikleri ve bunları [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]açıklamak için kullanılan bazı terminoloji ve kurallar hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Bağımlılık özellikleri örnekleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sınıflarda uygulanan bağımlılık özelliklerinin örnekleri, özelliği, <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.Control.Background%2A> de birçok başka özellik arasında bulunur. Bir sınıf tarafından sunulan her bağımlılık özelliği, aynı sınıfta <xref:System.Windows.DependencyProperty> sunulan karşılık gelen ortak statik bir alana sahiptir. Bu, Dependency özelliğine yönelik tanıtıcıdır. Tanımlayıcı, bir kural kullanılarak adlandırılır: dize `Property` eklenmiş olan Dependency özelliğinin adı. Örneğin, <xref:System.Windows.DependencyProperty> <xref:System.Windows.Controls.Control.Background%2A> özelliği içinkarşılıkgelentanımlayıcıalanı.<xref:System.Windows.Controls.Control.BackgroundProperty> Tanımlayıcı, kayıt sırasında bağımlılık özelliği hakkında bilgi depolar ve tanımlayıcı daha sonra, çağırma <xref:System.Windows.DependencyObject.SetValue%2A>gibi bağımlılık özelliğini içeren diğer işlemler için kullanılır.

[Bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)bölümünde belirtildiği gibi, içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tüm bağımlılık özellikleri (en fazla ekli özellikler hariç), "sarmalayıcı" uygulamasıyla aynı zamanda clr özellikleridir. Bu nedenle, koddan, diğer CLR özelliklerini kullandığınız şekilde sarmalayıcıları tanımlayan CLR erişimcileri çağırarak bağımlılık özelliklerini alabilir veya ayarlayabilirsiniz. Bağımlılık özelliklerinin bir tüketicisi olarak, temel alınan özellik sistemine bağlantı noktası olan <xref:System.Windows.DependencyObject> yöntemleri <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>genellikle kullanmayın. Bunun yerine, CLR özelliklerinin mevcut uygulaması, tanımlayıcı alanını uygun şekilde kullanarak <xref:System.Windows.DependencyObject.GetValue%2A> , <xref:System.Windows.DependencyObject.SetValue%2A> özelliğin `get` ve `set` sarmalayıcı uygulamalarının içinde zaten çağırılır. Kendi kendinize özel bir bağımlılık özelliği uygularken, sarmalayıcı benzer bir şekilde tanımlayacaksınız.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Bağımlılık özelliğini ne zaman uygulamanız gerekir?

Bir sınıf üzerinde bir özellik uyguladığınızda, sınıfınızın ' den <xref:System.Windows.DependencyObject>türettiği sürece, özelliğini bir <xref:System.Windows.DependencyProperty> tanımlayıcı ile geri yükleyebilirsiniz ve bu sayede bir bağımlılık özelliği yapabilirsiniz. Özelliğin bağımlılık özelliği olması her zaman gerekli veya uygun değildir ve senaryo gereksinimlerinize göre değişir. Bazen, özelliği özel bir alanla yedeklemenin tipik tekniği yeterlidir. Ancak, özelliği aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerde bir veya daha fazlasını desteklemek istediğinizde, bir bağımlılık özelliği olarak özelliğini uygulamalısınız:

- Özelliğin bir stilde ayarlanabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.

- Özelliğin veri bağlamayı desteklemesini istiyorsunuz. Veri bağlama bağımlılığı özellikleri hakkında daha fazla bilgi için bkz. [Iki denetimin özelliklerini bağlama](../data/how-to-bind-the-properties-of-two-controls.md).

- Özelliğin dinamik bir kaynak başvurusuyla ayarlanabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).

- Bir özellik değerini, öğe ağacındaki bir üst öğeden otomatik olarak devralmayı istiyorsunuz. Bu durumda, clr erişimi için bir <xref:System.Windows.DependencyProperty.RegisterAttached%2A> özellik sarmalayıcısı da oluştursanız bile yöntemiyle kaydolun. Daha fazla bilgi için bkz. [özellik değeri devralma](property-value-inheritance.md).

- Özelliğin Animatable olmasını istiyorsunuz. Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).

- Özellik sisteminin, özelliğin önceki değeri, özellik sistemi, ortam, veya Kullanıcı tarafından gerçekleştirilen eylemler tarafından ne zaman değiştirildiğini ya da stilleri okuyarak ve kullanarak rapor kullanmasını istersiniz. Özelliği, özellik meta verilerini kullanarak özellik sisteminin, özellik değerinin tanımlı olduğunu belirlediği her seferinde çağrılacak bir geri çağırma yöntemi belirtebilir. İlgili bir kavram Özellik değeri zorlamasının olması. Daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md).

- Bir özellik değerinin değiştirilmesinin, düzen sisteminin bir öğenin görsellerini yeniden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturmak için gerekli olup olmayacağını bildirmek gibi süreçler tarafından da kullanılan oluşturulan meta veri kurallarını kullanmak istiyorsunuz. Ya da türetilmiş sınıfların varsayılan değer gibi meta veri tabanlı özellikleri değiştirebilmeleri için meta veri geçersiz kılmalarını kullanmak isteyebilirsiniz.

- Özel bir denetimin özelliklerinin **Özellikler** penceresi düzenlemesi gibi VISUAL Studio WPF tasarımcı desteğini almasını istiyorsunuz. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).

Bu senaryoları incelediğinizde, tamamen yeni bir özellik uygulamak yerine var olan bir bağımlılık özelliğinin meta verilerini geçersiz kılarak senaryonuzu elde etmeyi de göz önünde bulundurmanız gerekir. Meta veri geçersiz kılmanın pratik olup olmadığı, senaryonuza ve bu senaryonun mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri ve sınıflarında uygulamaya ne kadar yakından benzediğini gösterir. Mevcut özelliklerde meta verileri geçersiz kılma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Bağımlılık özelliği tanımlama denetim listesi

Bağımlılık özelliği tanımlamak dört farklı kavramdan oluşur. Bu kavramların bazıları uygulamada tek bir kod satırı olarak birleştirildiğinden, bu kavramlar kesin yordamsal adımlar değildir.

- Seçim Bağımlılık özelliği için özellik meta verileri oluşturun.

- Özellik adını özellik sistemine kaydedin, bir sahip türü ve özellik değerinin türünü belirtin. Ayrıca, kullanılıyorsa özellik meta verilerini de belirtin.

- Bir <xref:System.Windows.DependencyProperty> tanımlayıcıyı sahip türünde bir `public` `static` alanolaraktanımlayın`readonly` .

- Adı Dependency özelliğinin adıyla eşleşen bir CLR "sarmalayıcı" özelliği tanımlayın. CLR "sarmalayıcı" özelliğinin `get` ve `set` erişimcilerini yedekleyen bağımlılık özelliğiyle bağlantı kurmak için uygulayın.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Özelliği özellik sistemiyle kaydetme

Özelliğin bir bağımlılık özelliği olması için, bu özelliği özellik sisteminin tuttuğu bir tabloya kaydetmeniz ve daha sonra özellik sistemi işlemleri için niteleyici olarak kullanılan benzersiz bir tanımlayıcı sağlamanız gerekir. Bu işlemler iç işlemler veya özellik sistemi API 'Leri çağıran kendi kodunuz olabilir. Özelliği kaydetmek için, <xref:System.Windows.DependencyProperty.Register%2A> yöntemini sınıfınızın gövdesinde (ancak herhangi bir üye tanımının dışında) çağırabilirsiniz. Tanımlayıcı alanı, dönüş değeri olarak <xref:System.Windows.DependencyProperty.Register%2A> Yöntem çağrısı tarafından da sağlanır. <xref:System.Windows.DependencyProperty.Register%2A> Çağrının diğer üye tanımlarının dışında yapılmasının nedeni, sınıfınızın bir parçası olarak türünde <xref:System.Windows.DependencyProperty> bir `public` `static` `readonly` alan atamak ve oluşturmak için bu dönüş değerini kullanmanız nedenidir. Bu alan, bağımlılık özelliği için tanımlayıcı olur.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Bağımlılık özelliği adı kuralları

Tüm ancak olağanüstü koşullarda izlemeniz gereken bağımlılık özellikleriyle ilgili adlandırma kuralları vardır.

Bağımlılık özelliğinin kendisi, bu örnekte olduğu gibi temel bir ada sahip olur, örneğin ilk parametresi <xref:System.Windows.DependencyProperty.Register%2A>olarak verilir. Bu ad, her kayıt türü içinde benzersiz olmalıdır. Temel türler aracılığıyla devralınan bağımlılık özellikleri, kayıt türünün zaten parçası olarak kabul edilir; devralınan özelliklerin adları yeniden kaydedilemez. Ancak, bağımlılık özelliği devralınmasa bile, bir bağımlılık özelliğinin sahibi olarak bir sınıfı eklemek için bir teknik vardır. Ayrıntılar için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).

Tanımlayıcı alanını oluşturduğunuzda, bu alanı, kaydettiğiniz özelliğin adıyla, artı sonekine `Property`göre adlandırın. Bu alan, bağımlılık özelliği için tanımlayıcdır ve daha sonra, herhangi bir dış kod erişiminde, kendi <xref:System.Windows.DependencyObject.SetValue%2A> kodunuzla ilgili diğer kod erişimlerinizi ve <xref:System.Windows.DependencyObject.GetValue%2A> bu özellik için bir giriş olarak bir giriş olarak kullanılır , özellik sistemi ve potansiyel olarak işlemcilere göre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

> [!NOTE]
> Sınıf gövdesinde Dependency özelliğinin tanımlanması tipik bir uygulama, ancak sınıf statik oluşturucusunda bir bağımlılık özelliği tanımlanması da mümkündür. Bağımlılık özelliğini başlatmak için birden fazla kod satırına ihtiyacınız varsa bu yaklaşım anlamlı hale gelebilir.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>"Sarmalayıcı" uygulama

<xref:System.Windows.DependencyObject.GetValue%2A> Sarmalayıcı uygulamanız `get` uygulamadave<xref:System.Windows.DependencyObject.SetValue%2A> uygulamada çağrılmalıdır (özgün kayıt çağrısı ve alan burada açıklık için de gösteriliyor). `set`

Tüm ancak olağanüstü durumlarda, sarmalayıcı uygulamalarınızın sırasıyla yalnızca <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> eylemleri gerçekleştirmesi gerekir. Bunun nedeni [XAML yükleme ve bağımlılık özellikleri](xaml-loading-and-dependency-properties.md)konu başlığında ele alınmıştır.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sınıflarda sağlanmış olan tüm mevcut genel bağımlılık özellikleri bu basit sarmalayıcı uygulama modelini kullanır; bağımlılık özelliklerinin çalışma özelliğinin büyük bir bölümünü özellik sisteminin bir davranışı veya Özellik meta verileri aracılığıyla zorlama veya özellik değişikliği geri çağırmaları gibi diğer kavramlar aracılığıyla uygulanır.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Yine kurala göre sarmalayıcı özelliğinin adı, seçilen ad ile aynı olmalıdır ve özelliği kaydedilen <xref:System.Windows.DependencyProperty.Register%2A> çağrının ilk parametresi olarak verilir. Özelliği kuralı izlemeiyorsa, bu tüm olası kullanımları devre dışı bırakmayabilir, ancak çeşitli önemli sorunlarıyla karşılaşırsınız:

- Stillerin ve şablonların belirli yönleri çalışmayacak.

- Çoğu araç ve tasarımcı, uygun bir şekilde serileştirmek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]için adlandırma kurallarına uymalıdır ya da özellik başına bir düzeyde Tasarımcı ortamı yardımını sağlamaktır.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Yükleyicinin geçerli uygulanması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , sarmalayıcıları tamamen atlar ve öznitelik değerlerini işlerken adlandırma kuralını kullanır. Daha fazla bilgi için bkz. [XAML yükleme ve bağımlılık özellikleri](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Yeni bir bağımlılık özelliği için özellik meta verileri

Bir bağımlılık özelliği kaydettiğinizde, özellik sistemi ile kayıt, özellik özelliklerini depolayan bir meta veri nesnesi oluşturur. Bu özelliklerin birçoğu, özelliği basit imzalarıyla <xref:System.Windows.DependencyProperty.Register%2A>kayıtlıysa ayarlanmış olan varsayılanlardır. Diğer imzaları <xref:System.Windows.DependencyProperty.Register%2A> , özelliği kaydettiğinizde istediğiniz meta verileri belirtmenize izin verir. Bağımlılık özellikleri için verilen en yaygın meta veriler, özelliği kullanan yeni örneklere uygulanan varsayılan bir değer vermektir.

Türetilmiş bir sınıfında <xref:System.Windows.FrameworkElement>bulunan bir bağımlılık özelliği oluşturuyorsanız, temel <xref:System.Windows.PropertyMetadata> sınıf yerine daha özelleştirilmiş meta veri sınıfını <xref:System.Windows.FrameworkPropertyMetadata> kullanabilirsiniz. <xref:System.Windows.FrameworkPropertyMetadata> Sınıf için Oluşturucu, bileşimde çeşitli meta veri özellikleri belirtebileceğiniz birkaç imzaya sahiptir. Yalnızca varsayılan değeri belirtmek istiyorsanız, türünde <xref:System.Object>tek bir parametre alan imzayı kullanın. Bu nesne parametresini, özelliği için türe özgü bir varsayılan değer olarak geçirin (belirtilen varsayılan değer, `propertyType` <xref:System.Windows.DependencyProperty.Register%2A> çağrıda parametre olarak belirttiğiniz tür olmalıdır).

İçin <xref:System.Windows.FrameworkPropertyMetadata>, özelliği için meta veri seçenek bayraklarını de belirtebilirsiniz. Bu bayraklar, kayıt sonrasında özellik meta verilerinde ayrık özelliklere dönüştürülür ve belirli koşulları, düzen altyapısı gibi diğer işlemlere iletmek için kullanılır.

#### <a name="setting-appropriate-metadata-flags"></a>Uygun meta veri bayraklarını ayarlama

- Özelliği ( [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]veya değerindeki değişiklikler) ' i etkiliyorsa ve özellikle de düzen sisteminin bir sayfada kendi öğelerini nasıl boyutlandırmalı ya da işlemesi gerektiğini etkiliyorsa, aşağıdaki bayraklardan birini veya birkaçını ayarlayın: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>Bu özellikte yapılan bir değişikliğin, kapsayan nesnenin üst öğe içinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] daha fazla veya daha az alan gerektirebileceği, işleme için değişiklik gerektirdiğini belirtir. Örneğin, bir "width" özelliği bu bayrak kümesine sahip olmalıdır.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>Bu özellikte yapılan bir değişikliğin, genellikle özel alanda değişiklik gerektirmeyen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , ancak alanın içindeki konumlandırmayı değiştiği anlamına gelen işleme değişikliğini gerektirdiğini gösterir. Örneğin, bir "hizalama" özelliği bu bayrak kümesine sahip olmalıdır.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>Düzen ve ölçüyü etkilemeyen, ancak başka bir işleme gerektirmeyecek başka bir değişikliğin oluştuğunu gösterir. Örneğin, "Arkaplan" gibi var olan bir öğenin rengini değiştiren bir özellik olabilir.

  - Bu bayraklar genellikle, özellik sistemi veya Düzen geri çağırmaları için kendi geçersiz kılma uygulamalarınız için meta verilerde bir protokol olarak kullanılır. <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> Örneğin, örneğin herhangi <xref:System.Windows.UIElement.InvalidateArrange%2A> `true` bir özelliği bir değer değişikliğini bildirirse ve meta verilerinde olduğugibi,çağıranbirgeriçağırmaişlemiolabilir.<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>

- Bazı özellikler, yukarıda bahsedilen gerekli boyuttaki değişikliklere göre yukarıdaki ve sonraki yollarla, kapsayan üst öğenin işleme özelliklerini etkileyebilir. Akış belge modelinde kullanılan <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> özelliktir. Bu özellik, bu özellikte yapılan değişikliklerin paragrafı içeren akış belgesinin genel işlemesini değiştirebildiği bir örnektir. Kendi <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> özelliklerindeki <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> benzer durumları belirlemek için veya kullanın.

- Varsayılan olarak, bağımlılık özellikleri veri bağlamayı destekler. Veri bağlama için gerçekçi bir senaryo olmadığı durumlarda veya büyük bir nesne için veri bağlamanın performansının bir sorun olarak tanındığından dolayı veri bağlamayı kasıtlı olarak devre dışı bırakabilirsiniz.

- Varsayılan olarak, bağımlılık özellikleri <xref:System.Windows.Data.Binding.Mode%2A> için veri bağlama varsayılan olarak <xref:System.Windows.Data.BindingMode.OneWay>olur. Bağlamayı her zaman bağlama örneği başına olacak <xref:System.Windows.Data.BindingMode.TwoWay> şekilde değiştirebilirsiniz; Ayrıntılar için bkz. [bağlamanın yönünü belirtme](../data/how-to-specify-the-direction-of-the-binding.md). Ancak bağımlılık özelliği yazarı olarak, özelliğin bağlama modunu varsayılan olarak kullanmasına <xref:System.Windows.Data.BindingMode.TwoWay> olanak seçebilirsiniz. Mevcut bir bağımlılık özelliğine <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>bir örnek; bu özellik <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> için senaryo, varsayılan tema stiliyle <xref:System.Windows.Controls.MenuItem> etkileşim kurma mantığının ve birleştirme özelliğinin bir örneğidir. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Özellik mantığı, diğer durum özelliklerine ve yöntem çağrılarına uygun olarak özelliğin durumunu korumak için yerel olarak veri bağlamayı kullanır. Varsayılan olarak bağlanan <xref:System.Windows.Data.BindingMode.TwoWay> başka bir örnek özelliği. <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>

- Ayrıca, <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> bayrağı ayarlayarak özel bir bağımlılık özelliğinde özellik devralmayı etkinleştirebilirsiniz. Özellik devralma, üst öğeler ve alt öğelerin ortak bir özelliği olan bir senaryo için yararlıdır ve alt öğelerin, bu belirli özellik değerinin üst öğe ile aynı değere ayarlanmış olması için mantıklı olmasını sağlar. Veri sunumu için önemli ana <xref:System.Windows.FrameworkElement.DataContext%2A>ayrıntı senaryosunu etkinleştirmek üzere bağlama işlemleri için kullanılan, örnek bir devredilebilir özelliği. Devralınabilir yapıldığında <xref:System.Windows.FrameworkElement.DataContext%2A> , tüm alt öğeler bu veri bağlamını de devralır. Özellik değeri devralımı nedeniyle, sayfada veya uygulama kökünde bir veri bağlamı belirtebilir ve tüm olası alt öğelerde bağlamalar için bunu belirtmeniz gerekmez. <xref:System.Windows.FrameworkElement.DataContext%2A>, devralmanın varsayılan değeri geçersiz kıldığını göstermek için de iyi bir örnektir; ancak her zaman belirli bir alt öğede yerel olarak ayarlanabilir; Ayrıntılar için bkz. [hiyerarşik verilerle ana ayrıntı modelini kullanma](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Özellik değeri devralımı olası bir performans maliyetine sahiptir ve bu nedenle, gelişigüzel kullanılmalıdır; Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).

- Bağımlılık özelliğinin, gezinme günlüğe kaydetme hizmetleri tarafından algılanıp algılanmadığını veya kullanılacağını belirtmek için bayrağıayarlayın.<xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> Özellik bir örnektir; günlük geçmişi gezinirken seçim denetiminde seçilen herhangi bir öğe kalıcı olmalıdır.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri

Salt okunurdur bir bağımlılık özelliği tanımlayabilirsiniz. Bununla birlikte, özelliği özellik sistemine kaydetme ve tanımlayıcıyı kullanıma sunma yordamı gibi, özelliğini salt okunurdur olarak nasıl tanımlayacağınızı belirleyen senaryolar biraz farklıdır. Daha fazla bilgi için bkz. [salt okuma bağımlılığı özellikleri](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri

Koleksiyon türü bağımlılık özelliklerine göz önünde bulundurmanız gereken bazı ek uygulama sorunları vardır. Ayrıntılar için bkz. [koleksiyon türü bağımlılık özellikleri](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Bağımlılık özelliği güvenlik konuları

Bağımlılık özellikleri genel özellikler olarak bildirilmelidir. Bağımlılık özelliği tanımlayıcı alanları ortak statik alanlar olarak bildirilmelidir. Diğer erişim düzeylerini (örneğin, korumalı) bildirmeye çalışırsanız bile, bağımlılık özelliğine her zaman özellik sistemi API 'Leri ile birlikte tanımlayıcı üzerinden erişilebilir. Korumalı bir tanımlayıcı alanı, <xref:System.Windows.LocalValueEnumerator>özellik sisteminin bir parçası olan meta veri raporlama veya değer belirleme API 'leri nedeniyle erişilebilir durumda olabilir. Daha fazla bilgi için bkz. [bağımlılık özelliği güvenliği](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Bağımlılık özellikleri ve sınıf oluşturucuları

Yönetilen kod programlamada genel bir ilke vardır (genellikle FxCop gibi kod çözümleme araçları tarafından zorlanır), sınıf oluşturucuların sanal yöntemleri çağırmamalıdır. Bunun nedeni, oluşturucuların türetilmiş bir sınıf oluşturucusunun temel başlatması olarak çağrılabilmesi ve sanal yönteminin Oluşturucu aracılığıyla girilmesi, oluşturulmakta olan nesne örneğinin tamamlanmamış bir başlatma durumunda meydana gelebilir. ' Dan <xref:System.Windows.DependencyObject>türetilmiş herhangi bir sınıftan türettiğinizde, özellik sisteminin kendisinin sanal yöntemleri dahili olarak çağırdığı ve açığa çıkardığı farkında olmalısınız. Bu sanal yöntemler, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistem hizmetlerinin bir parçasıdır. Yöntemlerin geçersiz kılınması, türetilmiş sınıfların değer belirlenmesine katılmasını sağlar. Çalışma zamanı başlatma ile ilgili olası sorunları önlemek için, belirli bir Oluşturucu modelini izlemeden, sınıfların oluşturucuları içinde bağımlılık özelliği değerlerini ayarlamamalısınız. Ayrıntılar için bkz. [DependencyObjects Için güvenli Oluşturucu desenleri](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)
- [XAML Yükleme ve Bağımlılık Özellikleri](xaml-loading-and-dependency-properties.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](safe-constructor-patterns-for-dependencyobjects.md)
