---
title: Özel Bağımlılık Özellikleri
description: Windows Presentation Foundation özellik uygulama adımlarını ve özelliğin performansını, kullanılabilirliğini veya çok yönlülüğünü geliştirme seçeneklerini öğrenin.
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
ms.openlocfilehash: b082340afb8b1a814fc5923126aa58183d43bc01
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168147"
---
# <a name="custom-dependency-properties"></a>Özel Bağımlılık Özellikleri

Bu konuda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , uygulama geliştiricilerinin ve bileşen yazarlarının özel bağımlılık özelliği oluşturmak isteyebileceğiniz nedenler açıklanmakta ve özelliğin performansı, kullanılabilirliği veya çok yönlülüğü iyileştirebilecek bazı uygulama seçenekleri de açıklanmaktadır.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Ön koşullar

Bu konuda, sınıflarda mevcut bağımlılık özelliklerinin bir tüketicisinin perspektifinden bağımlılık özelliklerini anladığınızı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md) konusunu okuduğunuzu varsaymış olursunuz. Bu konudaki örnekleri izlemek için, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamaların nasıl yazılacağını de anlamanız ve bilmeniz gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Bağımlılık özelliği nedir?

Aynı şekilde, bir bağımlılık özelliği olarak uygulayarak stil, veri bağlama, devralma, animasyonlar ve varsayılan değerleri desteklemek için ortak dil çalışma zamanı (CLR) özelliğinin ne olduğunu seçebilirsiniz. Bağımlılık özellikleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DependencyProperty.Register%2A> yöntemi çağırarak (veya <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> ) ve bir tanımlayıcı alan tarafından desteklenen özellik sistemiyle kaydedilen özelliklerdir <xref:System.Windows.DependencyProperty> . Bağımlılık özellikleri yalnızca türler tarafından kullanılabilir <xref:System.Windows.DependencyObject> , ancak <xref:System.Windows.DependencyObject> sınıf hiyerarşisinde oldukça yüksek olduğundan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ' de bulunan sınıfların çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özelliklerini destekleyebilir. Bağımlılık özellikleri ve bu SDK 'da bunları açıklamak için kullanılan bazı terminoloji ve kurallar hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Bağımlılık özellikleri örnekleri

Sınıflarda uygulanan bağımlılık özelliklerinin örnekleri, özelliği, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve <xref:System.Windows.Controls.TextBox.Text%2A> özelliği de birçok başka özellik arasında bulunur. Bir sınıf tarafından sunulan her bağımlılık özelliği, aynı sınıfta sunulan karşılık gelen ortak statik bir alana sahiptir <xref:System.Windows.DependencyProperty> . Bu, Dependency özelliğine yönelik tanıtıcıdır. Tanımlayıcı, bir kural kullanılarak adlandırılır: dize eklenmiş olan Dependency özelliğinin adı `Property` . Örneğin, <xref:System.Windows.DependencyProperty> özelliği için karşılık gelen tanımlayıcı alanı <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.BackgroundProperty> . Tanımlayıcı, kayıt sırasında bağımlılık özelliği hakkında bilgi depolar ve tanımlayıcı daha sonra, çağırma gibi bağımlılık özelliğini içeren diğer işlemler için kullanılır <xref:System.Windows.DependencyObject.SetValue%2A> .

[Bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)bölümünde belirtildiği gibi, içindeki tüm bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (en fazla ekli özellikler hariç), "sarmalayıcı" UYGULAMASıYLA aynı zamanda clr özellikleridir. Bu nedenle, koddan, diğer CLR özelliklerini kullandığınız şekilde sarmalayıcıları tanımlayan CLR erişimcileri çağırarak bağımlılık özelliklerini alabilir veya ayarlayabilirsiniz. Bağımlılık özelliklerinin bir tüketicisi olarak, <xref:System.Windows.DependencyObject> <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> temel alınan özellik sistemine bağlantı noktası olan yöntemleri ve genellikle kullanmayın. Bunun yerine, CLR özelliklerinin mevcut uygulaması, <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> `get` `set` tanımlayıcı alanını uygun şekilde kullanarak, özelliğin ve sarmalayıcı uygulamalarının içinde zaten çağırılır. Kendi kendinize özel bir bağımlılık özelliği uygularken, sarmalayıcı benzer bir şekilde tanımlayacaksınız.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Bağımlılık özelliğini ne zaman uygulamanız gerekir?

Bir sınıf üzerinde bir özellik uyguladığınızda, sınıfınızın ' den türettiği sürece <xref:System.Windows.DependencyObject> , özelliğini bir tanımlayıcı ile geri yükleyebilirsiniz <xref:System.Windows.DependencyProperty> ve bu sayede bir bağımlılık özelliği yapabilirsiniz. Özelliğin bağımlılık özelliği olması her zaman gerekli veya uygun değildir ve senaryo gereksinimlerinize göre değişir. Bazen, özelliği özel bir alanla yedeklemenin tipik tekniği yeterlidir. Ancak, özelliği aşağıdaki özelliklerde bir veya daha fazlasını desteklemek istediğinizde, bir bağımlılık özelliği olarak özelliğini uygulamalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :

- Özelliğin bir stilde ayarlanabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.

- Özelliğin veri bağlamayı desteklemesini istiyorsunuz. Veri bağlama bağımlılığı özellikleri hakkında daha fazla bilgi için bkz. [Iki denetimin özelliklerini bağlama](../data/how-to-bind-the-properties-of-two-controls.md).

- Özelliğin dinamik bir kaynak başvurusuyla ayarlanabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Bir özellik değerini, öğe ağacındaki bir üst öğeden otomatik olarak devralmayı istiyorsunuz. Bu durumda, <xref:System.Windows.DependencyProperty.RegisterAttached%2A> clr erişimi için bir özellik sarmalayıcısı da oluştursanız bile yöntemiyle kaydolun. Daha fazla bilgi için bkz. [özellik değeri devralma](property-value-inheritance.md).

- Özelliğin Animatable olmasını istiyorsunuz. Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).

- Özellik sisteminin, özelliğin önceki değeri, özellik sistemi, ortam, veya Kullanıcı tarafından gerçekleştirilen eylemler tarafından ne zaman değiştirildiğini ya da stilleri okuyarak ve kullanarak rapor kullanmasını istersiniz. Özelliği, özellik meta verilerini kullanarak özellik sisteminin, özellik değerinin tanımlı olduğunu belirlediği her seferinde çağrılacak bir geri çağırma yöntemi belirtebilir. İlgili bir kavram Özellik değeri zorlamasının olması. Daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md).

- Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik değerinin değiştirilmesinin, düzen sisteminin bir öğenin görsellerini yeniden oluşturmak için gerekli olup olmayacağını bildirmek gibi süreçler tarafından da kullanılan oluşturulan meta veri kurallarını kullanmak istiyorsunuz. Ya da türetilmiş sınıfların varsayılan değer gibi meta veri tabanlı özellikleri değiştirebilmeleri için meta veri geçersiz kılmalarını kullanmak isteyebilirsiniz.

- Özel bir denetimin özelliklerinin **Özellikler** penceresi düzenlemesi gibi VISUAL Studio WPF tasarımcı desteğini almasını istiyorsunuz. Daha fazla bilgi için bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md).

Bu senaryoları incelediğinizde, tamamen yeni bir özellik uygulamak yerine var olan bir bağımlılık özelliğinin meta verilerini geçersiz kılarak senaryonuzu elde etmeyi de göz önünde bulundurmanız gerekir. Meta veri geçersiz kılmanın pratik olup olmadığı, senaryonuza ve bu senaryonun mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri ve sınıflarında uygulamaya ne kadar yakından benzediğini gösterir. Mevcut özelliklerde meta verileri geçersiz kılma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Bağımlılık özelliği tanımlama denetim listesi

Bağımlılık özelliği tanımlamak dört farklı kavramdan oluşur. Bu kavramların bazıları uygulamada tek bir kod satırı olarak birleştirildiğinden, bu kavramlar kesin yordamsal adımlar değildir.

- Seçim Bağımlılık özelliği için özellik meta verileri oluşturun.

- Özellik adını özellik sistemine kaydedin, bir sahip türü ve özellik değerinin türünü belirtin. Ayrıca, kullanılıyorsa özellik meta verilerini de belirtin.

- Bir <xref:System.Windows.DependencyProperty> tanımlayıcıyı `public` `static` `readonly` sahip türünde bir alan olarak tanımlayın.

- Adı Dependency özelliğinin adıyla eşleşen bir CLR "sarmalayıcı" özelliği tanımlayın. CLR "sarmalayıcı" özelliğinin `get` ve `set` erişimcilerini yedekleyen bağımlılık özelliğiyle bağlantı kurmak için uygulayın.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Özelliği özellik sistemiyle kaydetme

Özelliğin bir bağımlılık özelliği olması için, bu özelliği özellik sisteminin tuttuğu bir tabloya kaydetmeniz ve daha sonra özellik sistemi işlemleri için niteleyici olarak kullanılan benzersiz bir tanımlayıcı sağlamanız gerekir. Bu işlemler iç işlemler veya özellik sistemi API 'Leri çağıran kendi kodunuz olabilir. Özelliği kaydetmek için, <xref:System.Windows.DependencyProperty.Register%2A> yöntemini sınıfınızın gövdesinde (ancak herhangi bir üye tanımının dışında) çağırabilirsiniz. Tanımlayıcı alanı <xref:System.Windows.DependencyProperty.Register%2A> , dönüş değeri olarak yöntem çağrısı tarafından da sağlanır. <xref:System.Windows.DependencyProperty.Register%2A>Çağrının diğer üye tanımlarının dışında yapılmasının nedeni, `public` `static` `readonly` sınıfınızın bir parçası olarak türünde bir alan atamak ve oluşturmak için bu dönüş değerini kullanmanız nedenidir <xref:System.Windows.DependencyProperty> . Bu alan, bağımlılık özelliği için tanımlayıcı olur.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Bağımlılık özelliği adı kuralları

Tüm ancak olağanüstü koşullarda izlemeniz gereken bağımlılık özellikleriyle ilgili adlandırma kuralları vardır.

Bağımlılık özelliğinin kendisi, bu örnekte olduğu gibi temel bir ada sahip olur, örneğin ilk parametresi olarak verilir <xref:System.Windows.DependencyProperty.Register%2A> . Bu ad, her kayıt türü içinde benzersiz olmalıdır. Temel türler aracılığıyla devralınan bağımlılık özellikleri, kayıt türünün zaten parçası olarak kabul edilir; devralınan özelliklerin adları yeniden kaydedilemez. Ancak, bağımlılık özelliği devralınmasa bile, bir bağımlılık özelliğinin sahibi olarak bir sınıfı eklemek için bir teknik vardır. Ayrıntılar için bkz. [bağımlılık özelliği meta verileri](dependency-property-metadata.md).

Tanımlayıcı alanını oluşturduğunuzda, bu alanı, kaydettiğiniz özelliğin adıyla, artı sonekine göre adlandırın `Property` . Bu alan, bağımlılık özelliği için olan tanımlayıcdır ve daha sonra, <xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyObject.GetValue%2A> kendi kodunuz tarafından, izin verilen herhangi bir harici kod erişimi, özellik sistemi ve potansiyel olarak işlemcilere göre herhangi bir kod erişimi için, daha sonra sarmalayıcılarda yapacağınız çağrı ve çağrılar için bir giriş olarak kullanılır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

> [!NOTE]
> Sınıf gövdesinde Dependency özelliğinin tanımlanması tipik bir uygulama, ancak sınıf statik oluşturucusunda bir bağımlılık özelliği tanımlanması da mümkündür. Bağımlılık özelliğini başlatmak için birden fazla kod satırına ihtiyacınız varsa bu yaklaşım anlamlı hale gelebilir.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>"Sarmalayıcı" uygulama

Sarmalayıcı uygulamanız <xref:System.Windows.DependencyObject.GetValue%2A> `get` uygulamada ve <xref:System.Windows.DependencyObject.SetValue%2A> `set` uygulamada çağrılmalıdır (özgün kayıt çağrısı ve alan burada açıklık için de gösteriliyor).

Tüm ancak olağanüstü durumlarda, sarmalayıcı uygulamalarınızın <xref:System.Windows.DependencyObject.GetValue%2A> sırasıyla yalnızca ve eylemleri gerçekleştirmesi gerekir <xref:System.Windows.DependencyObject.SetValue%2A> . Bunun nedeni [XAML yükleme ve bağımlılık özellikleri](xaml-loading-and-dependency-properties.md)konu başlığında ele alınmıştır.

Sınıflarda sağlanmış olan tüm mevcut genel bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu basit sarmalayıcı uygulama modelini kullanır; bağımlılık özelliklerinin büyük bir bölümünü özellik sisteminin bir davranışı temel alır ya da özellik meta verileri aracılığıyla zorlama ya da özellik değişikliği geri çağırmaları gibi diğer kavramlar aracılığıyla uygulanabilir.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Yine kurala göre sarmalayıcı özelliğinin adı, seçilen ad ile aynı olmalıdır ve özelliği kaydedilen çağrının ilk parametresi olarak verilir <xref:System.Windows.DependencyProperty.Register%2A> . Özelliği kuralı izlemeiyorsa, bu tüm olası kullanımları devre dışı bırakmayabilir, ancak çeşitli önemli sorunlarıyla karşılaşırsınız:

- Stillerin ve şablonların belirli yönleri çalışmayacak.

- Çoğu araç ve tasarımcı, uygun bir şekilde serileştirmek için adlandırma kurallarına uymalıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ya da özellik başına bir düzeyde Tasarımcı ortamı yardımını sağlamaktır.

- Yükleyicinin geçerli uygulanması, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sarmalayıcıları tamamen atlar ve öznitelik değerlerini işlerken adlandırma kuralını kullanır. Daha fazla bilgi için bkz. [XAML yükleme ve bağımlılık özellikleri](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Yeni bir bağımlılık özelliği için özellik meta verileri

Bir bağımlılık özelliği kaydettiğinizde, özellik sistemi ile kayıt, özellik özelliklerini depolayan bir meta veri nesnesi oluşturur. Bu özelliklerin birçoğu, özelliği basit imzalarıyla kayıtlıysa ayarlanmış olan varsayılanlardır <xref:System.Windows.DependencyProperty.Register%2A> . Diğer imzaları <xref:System.Windows.DependencyProperty.Register%2A> , özelliği kaydettiğinizde istediğiniz meta verileri belirtmenize izin verir. Bağımlılık özellikleri için verilen en yaygın meta veriler, özelliği kullanan yeni örneklere uygulanan varsayılan bir değer vermektir.

Türetilmiş bir sınıfında bulunan bir bağımlılık özelliği oluşturuyorsanız <xref:System.Windows.FrameworkElement> , <xref:System.Windows.FrameworkPropertyMetadata> temel sınıf yerine daha özelleştirilmiş meta veri sınıfını kullanabilirsiniz <xref:System.Windows.PropertyMetadata> . Sınıf için Oluşturucu, <xref:System.Windows.FrameworkPropertyMetadata> bileşimde çeşitli meta veri özellikleri belirtebileceğiniz birkaç imzaya sahiptir. Yalnızca varsayılan değeri belirtmek istiyorsanız, türünde tek bir parametre alan imzayı kullanın <xref:System.Object> . Bu nesne parametresini, özelliği için türe özgü bir varsayılan değer olarak geçirin (belirtilen varsayılan değer, çağrıda parametre olarak belirttiğiniz tür olmalıdır `propertyType` <xref:System.Windows.DependencyProperty.Register%2A> ).

İçin <xref:System.Windows.FrameworkPropertyMetadata> , özelliği için meta veri seçenek bayraklarını de belirtebilirsiniz. Bu bayraklar, kayıt sonrasında özellik meta verilerinde ayrık özelliklere dönüştürülür ve belirli koşulları, düzen altyapısı gibi diğer işlemlere iletmek için kullanılır.

#### <a name="setting-appropriate-metadata-flags"></a>Uygun meta veri bayraklarını ayarlama

- Özelliği (veya değerindeki değişiklikler) [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' i etkiliyorsa ve özellikle de düzen sisteminin bir sayfada kendi öğelerini nasıl boyutlandırmalı ya da işlemesi gerektiğini etkiliyorsa, aşağıdaki bayraklardan birini veya birkaçını ayarlayın: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> , <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> , <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> .

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>Bu özellikte yapılan bir değişikliğin, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kapsayan nesnenin üst öğe içinde daha fazla veya daha az alan gerektirebileceği, işleme için değişiklik gerektirdiğini belirtir. Örneğin, bir "width" özelliği bu bayrak kümesine sahip olmalıdır.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>Bu özellikte yapılan bir değişikliğin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , genellikle özel alanda değişiklik gerektirmeyen, ancak alanın içindeki konumlandırmayı değiştiği anlamına gelen işleme değişikliğini gerektirdiğini gösterir. Örneğin, bir "hizalama" özelliği bu bayrak kümesine sahip olmalıdır.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>Düzen ve ölçüyü etkilemeyen, ancak başka bir işleme gerektirmeyecek başka bir değişikliğin oluştuğunu gösterir. Örneğin, "Arkaplan" gibi var olan bir öğenin rengini değiştiren bir özellik olabilir.

  - Bu bayraklar genellikle, özellik sistemi veya Düzen geri çağırmaları için kendi geçersiz kılma uygulamalarınız için meta verilerde bir protokol olarak kullanılır. Örneğin, örneğin <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> <xref:System.Windows.UIElement.InvalidateArrange%2A> herhangi bir özelliği bir değer değişikliğini bildirirse ve <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> meta verilerinde olduğu gibi, çağıran bir geri çağırma işlemi olabilir `true` .

- Bazı özellikler, yukarıda bahsedilen gerekli boyuttaki değişikliklere göre yukarıdaki ve sonraki yollarla, kapsayan üst öğenin işleme özelliklerini etkileyebilir. <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A>Akış belge modelinde kullanılan özelliktir. Bu özellik, bu özellikte yapılan değişikliklerin paragrafı içeren akış belgesinin genel işlemesini değiştirebildiği bir örnektir. <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> Kendi özelliklerindeki benzer durumları belirlemek için veya kullanın.

- Varsayılan olarak, bağımlılık özellikleri veri bağlamayı destekler. Veri bağlama için gerçekçi bir senaryo olmadığı durumlarda veya büyük bir nesne için veri bağlamanın performansının bir sorun olarak tanındığından dolayı veri bağlamayı kasıtlı olarak devre dışı bırakabilirsiniz.

- Varsayılan olarak, bağımlılık özellikleri için veri bağlama varsayılan olarak <xref:System.Windows.Data.Binding.Mode%2A> olur <xref:System.Windows.Data.BindingMode.OneWay> . Bağlamayı her zaman <xref:System.Windows.Data.BindingMode.TwoWay> bağlama örneği başına olacak şekilde değiştirebilirsiniz; Ayrıntılar için bkz. [bağlamanın yönünü belirtme](../data/how-to-specify-the-direction-of-the-binding.md). Ancak bağımlılık özelliği yazarı olarak, özelliğin <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modunu varsayılan olarak kullanmasına olanak seçebilirsiniz. Mevcut bir bağımlılık özelliğine bir örnek <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType> ; Bu özellik için senaryo, <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> <xref:System.Windows.Controls.MenuItem> varsayılan tema stiliyle etkileşim kurma mantığının ve birleştirme özelliğinin bir örneğidir. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>Özellik mantığı, diğer durum özelliklerine ve yöntem çağrılarına uygun olarak özelliğin durumunu korumak için yerel olarak veri bağlamayı kullanır. Varsayılan olarak bağlanan başka bir örnek özelliği <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> .

- Ayrıca, bayrağı ayarlayarak özel bir bağımlılık özelliğinde özellik devralmayı etkinleştirebilirsiniz <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> . Özellik devralma, üst öğeler ve alt öğelerin ortak bir özelliği olan bir senaryo için yararlıdır ve alt öğelerin, bu belirli özellik değerinin üst öğe ile aynı değere ayarlanmış olması için mantıklı olmasını sağlar. <xref:System.Windows.FrameworkElement.DataContext%2A>Veri sunumu için önemli ana ayrıntı senaryosunu etkinleştirmek üzere bağlama işlemleri için kullanılan, örnek bir devredilebilir özelliği. Devralınabilir yapıldığında <xref:System.Windows.FrameworkElement.DataContext%2A> , tüm alt öğeler bu veri bağlamını de devralır. Özellik değeri devralımı nedeniyle, sayfada veya uygulama kökünde bir veri bağlamı belirtebilir ve tüm olası alt öğelerde bağlamalar için bunu belirtmeniz gerekmez. <xref:System.Windows.FrameworkElement.DataContext%2A>, devralmanın varsayılan değeri geçersiz kıldığını göstermek için de iyi bir örnektir; ancak her zaman belirli bir alt öğede yerel olarak ayarlanabilir; Ayrıntılar için bkz. [hiyerarşik verilerle ana ayrıntı modelini kullanma](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Özellik değeri devralımı olası bir performans maliyetine sahiptir ve bu nedenle, gelişigüzel kullanılmalıdır; Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).

- <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal>Bağımlılık özelliğinin, gezinme günlüğe kaydetme hizmetleri tarafından algılanıp algılanmadığını veya kullanılacağını belirtmek için bayrağı ayarlayın. Özellik bir örnektir <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> ; günlük geçmişi gezinirken seçim denetiminde seçilen herhangi bir öğe kalıcı olmalıdır.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri

Salt okunurdur bir bağımlılık özelliği tanımlayabilirsiniz. Bununla birlikte, özelliği özellik sistemine kaydetme ve tanımlayıcıyı kullanıma sunma yordamı gibi, özelliğini salt okunurdur olarak nasıl tanımlayacağınızı belirleyen senaryolar biraz farklıdır. Daha fazla bilgi için bkz. [salt okuma bağımlılığı özellikleri](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri

Koleksiyon türü bağımlılık özelliklerine göz önünde bulundurmanız gereken bazı ek uygulama sorunları vardır. Ayrıntılar için bkz. [koleksiyon türü bağımlılık özellikleri](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Bağımlılık özelliği güvenlik konuları

Bağımlılık özellikleri genel özellikler olarak bildirilmelidir. Bağımlılık özelliği tanımlayıcı alanları ortak statik alanlar olarak bildirilmelidir. Diğer erişim düzeylerini (örneğin, korumalı) bildirmeye çalışırsanız bile, bağımlılık özelliğine her zaman özellik sistemi API 'Leri ile birlikte tanımlayıcı üzerinden erişilebilir. Korumalı bir tanımlayıcı alanı, özellik sisteminin bir parçası olan meta veri raporlama veya değer belirleme API 'Leri nedeniyle erişilebilir durumda olabilir <xref:System.Windows.LocalValueEnumerator> . Daha fazla bilgi için bkz. [bağımlılık özelliği güvenliği](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Bağımlılık özellikleri ve sınıf oluşturucuları

Yönetilen kod programlamada genel bir ilke vardır (genellikle FxCop gibi kod çözümleme araçları tarafından zorlanır), sınıf oluşturucuların sanal yöntemleri çağırmamalıdır. Bunun nedeni, oluşturucuların türetilmiş bir sınıf oluşturucusunun temel başlatması olarak çağrılabilmesi ve sanal yönteminin Oluşturucu aracılığıyla girilmesi, oluşturulmakta olan nesne örneğinin tamamlanmamış bir başlatma durumunda meydana gelebilir. ' Dan türetilmiş herhangi bir sınıftan türettiğinizde <xref:System.Windows.DependencyObject> , özellik sisteminin kendisinin sanal yöntemleri dahili olarak çağırdığı ve açığa çıkardığı farkında olmalısınız. Bu sanal yöntemler, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistem hizmetlerinin bir parçasıdır. Yöntemlerin geçersiz kılınması, türetilmiş sınıfların değer belirlenmesine katılmasını sağlar. Çalışma zamanı başlatma ile ilgili olası sorunları önlemek için, belirli bir Oluşturucu modelini izlemeden, sınıfların oluşturucuları içinde bağımlılık özelliği değerlerini ayarlamamalısınız. Ayrıntılar için bkz. [DependencyObjects Için güvenli Oluşturucu desenleri](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](dependency-property-security.md)
- [XAML Yükleme ve Bağımlılık Özellikleri](xaml-loading-and-dependency-properties.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](safe-constructor-patterns-for-dependencyobjects.md)
