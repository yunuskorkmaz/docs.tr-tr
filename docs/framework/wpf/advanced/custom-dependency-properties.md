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
ms.openlocfilehash: f15490417d54121c750e2ea918820c5cb717002e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861522"
---
# <a name="custom-dependency-properties"></a>Özel Bağımlılık Özellikleri

Bu konuda, nedenleri açıklanmaktadır, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama geliştiricileri ve bileşen yazarları özel bağımlılık özelliği oluşturmak isteyebilirsiniz ve performansı artırmak bazı uygulama seçenekleri yanı sıra uygulama adımlarını açıklar. Kullanılabilirlik veya çok yönlülük özelliği.

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar

Bu konu, üzerinde bir tüketici mevcut bağımlılık özellikleri perspektifinden bağımlılık özellikleri anladığınızı varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) konu. Bu konudaki örnekleri izlemek için de anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.

<a name="whatis"></a>
## <a name="what-is-a-dependency-property"></a>Bağımlılık özelliği nedir?

Aksi takdirde ne olacağını etkinleştirebilirsiniz bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bağımlılık özelliği olarak uygulayarak stil, veri bağlama, devralma, animasyonları ve varsayılan değerleri desteklemek için özelliği. Bağımlılık özellikleri ile kaydedilen özellikleridir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağırarak özellik sistemi <xref:System.Windows.DependencyProperty.Register%2A> yöntemi (veya <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), ve tarafından desteklenen bir <xref:System.Windows.DependencyProperty> tanımlayıcı alanı. Bağımlılık özellikleri yalnızca kullanılabilir <xref:System.Windows.DependencyObject> türleri, ancak <xref:System.Windows.DependencyObject> oldukça yüksek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğunu bulunan sınıfları için sınıf hiyerarşisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri destekler. Bağımlılık özellikleri ve bazı terimler ve bunları bu tanımlamak için kullanılan kuralları hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).

<a name="example_dp"></a>
## <a name="examples-of-dependency-properties"></a>Örnekleri bağımlılık özellikleri

Örnekler üzerinde uygulanan bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıflarını <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve <xref:System.Windows.Controls.TextBox.Text%2A> yanı sıra diğer birçok özelliği. Bir sınıf tarafından kullanıma sunulan her bir bağımlılık özelliği karşılık gelen bir genel statik alan türü olan <xref:System.Windows.DependencyProperty> kullanıma sunulan bu aynı sınıf. Bağımlılık özelliği tanıtıcısıdır. Bir kural kullanarak tanımlayıcı adlı: bağımlılık özelliği dizesiyle adını `Property` eklenmiş. Örneğin, karşılık gelen <xref:System.Windows.DependencyProperty> tanımlayıcı alanı <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.Control.BackgroundProperty>. Kayıtlı olduğu ve tanımlayıcı ardından daha sonra arama gibi bir bağımlılık özelliği ile ilgili diğer işlemleri için kullanılan tanımlayıcı bağımlılık özelliği hakkında bilgi depolar <xref:System.Windows.DependencyObject.SetValue%2A>.

Belirtildiği gibi [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md), tüm bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (dışında en iliştirilmiş özellikler) olan ayrıca [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri nedeniyle "sarmalayıcı" uygulaması. Bu nedenle, koddan alabilir veya çağırarak bağımlılık özelliklerini ayarlama [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] sarmalayıcıları diğer kullanacağınız aynı şekilde tanımlayan erişimcileri [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri. Kurulan bağımlılık özellikleri tüketici olarak genellikle kullanmanızı <xref:System.Windows.DependencyObject> yöntemleri <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>, temel alınan özellik sistemi için bağlantı noktası olduğu. Bunun yerine, mevcut uygulamasını [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri zaten çağrıldı <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> içinde `get` ve `set` özelliğin tanımlayıcı alanı uygun şekilde kullanarak kapsayıcı uygulamaları . Özel bağımlılık özelliği kendiniz gerçekleştiriyorsanız, benzer şekilde sarmalayıcısını tanımlayan.

<a name="backing_with_dp"></a>
## <a name="when-should-you-implement-a-dependency-property"></a>Ne zaman bir bağımlılık özelliği uygulamanız gerekir?

Uyguladığınızda bir özelliği bir sınıfta, sınıfın türetildiği sürece <xref:System.Windows.DependencyObject>, özelliğinizi ile yedekleme seçeneğine sahip bir <xref:System.Windows.DependencyProperty> tanımlayıcısı ve bu nedenle bir bağımlılık özelliği yapmak için. Bağımlılık özelliği, özellik sahip her zaman uygun değildir ve senaryo gereksinimlerinize bağlıdır. Bazı durumlarda, özel bir alan, özelliği yedekleyen tipik tekniği yeterlidir. Bir veya daha fazlasını desteklemek için özellik istediğinizde ancak özelliğinizi bağımlılık özelliği olarak uygulamalıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri:

-   Bir style'nın ayarlanabilir özelliğini kullanmanız gerekir. Daha fazla bilgi için [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md).

-   Veri bağlamayı destekleyen özelliğini kullanmanız gerekir. Veri bağlama bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [özellikleri, iki denetim bağlama](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).

-   Dinamik kaynak başvuru ile ayarlanabilir özelliğini kullanmanız gerekir. Daha fazla bilgi için [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).

-   Bir özellik değeri otomatik olarak öğe ağacındaki bir üst öğeden devralır istiyorsunuz. Bu durumda, kaydolmalı <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi için özellik sarmalayıcı oluşturabilir olsa bile [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] erişim. Daha fazla bilgi için [özellik değeri kalıtımı](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

-   Özelliğinizi canlandırılabilir olmasını istediğiniz. Daha fazla bilgi için [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).

-   Özellik sistemi, ortam veya kullanıcı ya da okuma ve stilleri kullanarak gerçekleştirilen eylemleri tarafından özelliğinin önceki değeri değiştirildiğinde özellik sistemi rapor için istediğiniz. Özellik meta verileri kullanarak, özellik sistemi, özellik değeri kesin bir şekilde değiştirildi belirler. her zaman çağrılacak bir geri çağırma yöntemi, özelliği belirtebilirsiniz. Özellik değeri zorlama buna ilgili bir kavramdır. Daha fazla bilgi için [bağımlılık özelliği geri aramaları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).

-   Tarafından kullanılan yerleşik meta verileri kuralları kullanmak istediğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsellerin bir öğe için yeniden oluşturmak için Düzen sistemi özellik değerini değiştirmek istemeniz gerekir olup raporlama gibi işlemler. Veya türetilmiş sınıflar meta veri tabanlı özellikleri gibi varsayılan değer değiştirebilmeniz meta verileri geçersiz kılmaları kullanabilmek istiyorsunuz.

-   İstediğiniz gibi Visual Studio WPF Tasarımcısı almak için özel bir denetimin özelliklerini destekleyen **özellikleri** penceresi düzenleme. Daha fazla bilgi için [denetim yazmaya genel bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

Bu senaryolar incelediğinizde, senaryonuz var olan bir bağımlılık özelliği meta verileri geçersiz kılma yerine tamamen yeni bir özellik uygulama elde edebileceğiniz olup olmadığını da düşünmelisiniz. Meta verileri geçersiz kılma pratik olup kendi senaryonuza ve bu senaryonun varolan uygulama ne kadar yakın benzer bağlıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri ve sınıfları. Mevcut özellikler meta verileri geçersiz kılma hakkında daha fazla bilgi için bkz. [bağımlılık özelliği meta verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

<a name="checklist"></a>
## <a name="checklist-for-defining-a-dependency-property"></a>Bağımlılık özelliği tanımlamak için Denetim listesi

Bağımlılık özelliği tanımlama dört farklı kavramlarını oluşur. Bunların bazılarını, tek satırlık bir uygulamada kod olarak birleştirilen sonlandırmak için bu kavramları mutlaka katı yordamsal adımlar değildir:

-   (İsteğe bağlı) Bağımlılık özelliği için özellik meta verileri oluşturun.

-   Özellik adına sahip türü ve özellik değeri türünü belirten özellik sistemi ile kaydedin. Ayrıca kullandıysanız özellik meta verileri belirtin.

-   Tanımlayan bir <xref:System.Windows.DependencyProperty> tanımlayıcı olarak bir `public` `static` `readonly` alanına sahip türü.

-   Tanımlayan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" özellik adı ile eşleşen bağımlılık özelliğinin adı. Uygulama [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" özelliğin `get` ve `set` yedekler, bağımlılık özelliği ile bağlanmak için erişimcileri.

<a name="registering"></a>
### <a name="registering-the-property-with-the-property-system"></a>Özellik sistemi ile özelliği kaydetme

Bağımlılık özelliği olarak, bir özellik için sırada bu özellik özellik sistemi tarafından korunan bir tabloya kaydedin ve niteleyici sonraki özelliği sistem işlemleri için kullanılan benzersiz bir tanımlayıcı vermek gerekir. Bu işlemlerin iç işlemler ya da kendi kodunuzu arama özellik sistemi olabilir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Arama özelliği kaydetmek için <xref:System.Windows.DependencyProperty.Register%2A> sınıfınıza (sınıf içinde ancak herhangi bir üye tanımı dışında) gövdesi içinde yöntemi. Tanımlayıcı alan ayrıca tarafından sağlanan <xref:System.Windows.DependencyProperty.Register%2A> dönüş değeri olarak bir yöntem çağrısı. Bunun nedeni, <xref:System.Windows.DependencyProperty.Register%2A> çağrı yapılır dışında diğer üye tanımları olduğundan bu dönüş değeri atamak ve oluşturmak için kullandığınız bir `public` `static` `readonly` alan türü <xref:System.Windows.DependencyProperty> sınıfınızın bir parçası olarak. Bu alan, bağımlılık özelliği için olan tanımlayıcıyla olur.

[!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>
### <a name="dependency-property-name-conventions"></a>Bağımlılık özelliği adı kuralları

Tüm ancak olağanüstü durumlarda izlemeniz gereken bir bağımlılık özellikleri ile ilgili kurulan adlandırma kuralları vardır.

Bağımlılık özelliği ilk parametresi olarak verilen bu örnekte olduğu gibi "AquariumGraphic" temel bir adı vardır <xref:System.Windows.DependencyProperty.Register%2A>. Bu ad, her bir kayıt türü içinde benzersiz olmalıdır. Bağımlılık özellikleri aracılığıyla temel tür devralınan zaten kayıt türünün bir parçası olarak değerlendirilir; devralınan özellik adlarını yeniden kaydedilemez. Ancak, bile, bağımlılık özelliği değil devralındığında, bir bağımlılık özelliği sahibi olarak sınıf ekleme için bir yöntem yoktur; Ayrıntılar için bkz [bağımlılık özelliği meta verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

Tanımlayıcı alanı oluşturduğunuzda, ve bir son eke kayıtlı Bu alan özelliğinin adıyla ad `Property`. Bu alan, bağımlılık özelliği tanımlayıcısıdır ve daha sonra için girdi olarak kullanılacak <xref:System.Windows.DependencyObject.SetValue%2A> ve <xref:System.Windows.DependencyObject.GetValue%2A> nde yaptığınız tüm diğer kod erişim özelliği, kendi kod tarafından herhangi bir dış kod erişim tarafından sarmalayıcılar, çağrıları izin ver , özellik sistemi ve potansiyel olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci.

> [!NOTE]
> Bağımlılık özelliği sınıf gövdesine tanımlama tipik uygulamadır, ancak sınıfı statik oluşturucuda bir bağımlılık özelliği tanımlamak da mümkündür. Bağımlılık özelliği başlatmak için kod birden fazla satır gerekiyorsa bu yaklaşım mantıklı olabilir.

<a name="wrapper1"></a>
### <a name="implementing-the-wrapper"></a>"Sarmalayıcı" uygulama

Sarmalayıcı uygulamanız çağırmalıdır <xref:System.Windows.DependencyObject.GetValue%2A> içinde `get` uygulaması ve <xref:System.Windows.DependencyObject.SetValue%2A> içinde `set` uygulama (özgün kayıt çağrısı ve alan burada gösterilen çok daha anlaşılır olması için).

Tüm olağanüstü durumlarda, kapsayıcı uygulamaları yalnızca gerçekleştirmeniz gereken <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> Eylemler, sırasıyla. Bunun nedeni, konu başlığı altında açıklanan [XAML yükleme ve bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).

Üzerinde sağlanan tüm varolan genel bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları bu basit sarmalayıcı uygulama modeli kullanın; bağımlılık özelliklerinin nasıl çalıştığını karmaşıklığı çoğu ya da doğal olarak özellik sistemi davranışını veya özellik meta verileri üzerinden geri çağırmaları zorlama veya özelliği değiştirmek gibi diğer kavramlar uygulanır.

[!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Kural gereği, sarmalayıcı özelliğin adı seçilen ve ilk parametresi olarak belirtilen adıyla aynı yeniden olmalıdır <xref:System.Windows.DependencyProperty.Register%2A> özelliği kayıtlı arama. Özelliğinizi kuralı izlemiyorsa, bu mutlaka tüm olası kullanımı devre dışı bırakmaz ancak birkaç önemli sorunlar karşılaşırsınız:

-   Stilleri ve şablonları bazı yönlerini çalışmaz.

-   Çoğu araç ve tasarımcılar düzgün bir şekilde serileştirmek için adlandırma kuralları durumda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veya bir özelliğe düzeyinde Tasarımcı ortam Yardım sağlamak için.

-   Geçerli uygulaması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyici sarmalayıcıları tamamen atlar ve öznitelik değerleri işlerken adlandırma kuralı temelinde kullanır. Daha fazla bilgi için [XAML yükleme ve bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>
### <a name="property-metadata-for-a-new-dependency-property"></a>Yeni bir bağımlılık özelliği için özellik meta verileri

Bağımlılık özelliği kaydolduğunuzda, kayıt özellik sistemi aracılığıyla özelliği özellikleriyle depolayan bir meta veri nesnesi oluşturur. Bu özelliklerin çoğu özellik ile basit imzalarını kayıtlıysa, ayarlanan varsayılanlara sahiptir <xref:System.Windows.DependencyProperty.Register%2A>. Diğer imzalarını <xref:System.Windows.DependencyProperty.Register%2A> özelliği kaydetme gibi istediğiniz meta verileri belirlemenize olanak tanır. Bağımlılık özellikleri için belirtilen en yaygın meta veriler, bunları özelliği kullanan yeni örneklerinde uygulanan varsayılan bir değer vermektir.

Var olan bir bağımlılık özelliği türetilmiş bir sınıf oluşturuyorsanız <xref:System.Windows.FrameworkElement>, daha özel meta veri sınıfının kullanabileceğiniz <xref:System.Windows.FrameworkPropertyMetadata> temel yerine <xref:System.Windows.PropertyMetadata> sınıfı. Oluşturucusu <xref:System.Windows.FrameworkPropertyMetadata> sınıfında belirtebileceğiniz çeşitli meta veri özelliklerini birlikte birkaç imzalar. Yalnızca varsayılan değeri belirtmek istiyorsanız, tek bir parametre türü alan imza kullanmak <xref:System.Object>. Bu nesne parametresi, bir özellik için türe özgü varsayılan değer olarak geçirin (sağlanan varsayılan değer olarak sağlanan türü olmalıdır `propertyType` parametresinde <xref:System.Windows.DependencyProperty.Register%2A> arayın).

İçin <xref:System.Windows.FrameworkPropertyMetadata>, özellik için meta verileri seçeneği bayrakları de belirtebilirsiniz. Bu bayraklar özellik meta veriler ayrı özellikleri kayıt sonrasında dönüştürülür ve yerleşim altyapısı gibi diğer işlemleri için belirli koşullar iletişim kurmak için kullanılır.

#### <a name="setting-appropriate-metadata-flags"></a>Ayar uygun meta verileri bayrakları

-   Özellik (veya değişiklikleri değeri) etkiliyorsa [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], düzen sistemi boyutu veya bir sayfasında, öğe işleme nasıl özellikle etkiler bir veya daha fazla aşağıdaki bayraklarını ayarlayın: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> Bu özellik için bir değişiklik için bir değişiklik yapılması gerektiğini belirtir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] burada içeren nesne gerektirebilecek daha az veya üst içine boşluk işleme. Örneğin, "Width" özelliği bu bayrağı ayarlanmış olması gerekir.

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> Bu özellik için bir değişiklik için bir değişiklik yapılması gerektiğini belirtir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] genellikle işleme ayrılmış alanı bir değişiklik gerektirmez, ancak içine boşluk konumlandırma değiştiğini gösterir. Örneğin, "Hizalama" özelliği bu bayrağı ayarlanmış olması gerekir.

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> gösteren başka bir değişiklik oluştuğunu düzeni ve ölçü etkilemez, ancak başka bir işleme gerektirir. Bir örnek, "Arka plan" gibi var olan öğenin rengini değiştiren bir özelliği olabilir.

    -   Bu bayraklar genellikle meta verilerinde bir protokol olarak kendi özellik sistemi veya Düzen geri çağırmaları geçersiz kılma uygulamaları için kullanılır. Örneğin, sahip olabileceğiniz bir <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> çağıracak bir geri çağırma <xref:System.Windows.UIElement.InvalidateArrange%2A> örneğinin herhangi bir özellik değeri değişiklik raporları ve sahip <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> olarak `true` meta.

-   Bazı özellikler işleme özelliklerini içeren üst öğenin, yukarıda belirtilen gerekli boyutundaki değişiklikleri sunmayan şekilde etkileyebilir. Bir örnek <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> bu özellik değişiklikleri genel işleme paragraf içeren akış belgenin burada değiştirebilirsiniz akış belge modelinde kullanılan özellik. Kullanım <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> veya <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> benzer durumlarda kendi özellikleri tanımlamak için.

-   Varsayılan olarak, bağımlılık özellikleri veri bağlamayı destekler. Kasıtlı olarak çalışmaları için veri bağlama, veri bağlama için gerçekçi bir senaryo olduğunda ya da veri bağlama büyük bir nesne için performans bir sorun kabul edilen yerlerde devre dışı bırakabilirsiniz.

-   Varsayılan olarak, veri bağlama <xref:System.Windows.Data.Binding.Mode%2A> bağımlılık özellikleri varsayılan olarak <xref:System.Windows.Data.BindingMode.OneWay>. Her zaman bağlama olacak şekilde değiştirebilirsiniz <xref:System.Windows.Data.BindingMode.TwoWay> bağlama örnek başına; Ayrıntılar için bkz. [bağlama yönünü belirtme](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md). Ancak bağımlılık özelliği yazar olarak kullanma özelliği yapmak seçebileceğiniz <xref:System.Windows.Data.BindingMode.TwoWay> varsayılan bağlama modu. Mevcut bir bağımlılık özelliği örneğidir <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; senaryo için bu özelliği olan <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> mantığı ve birleştirme, ayarı <xref:System.Windows.Controls.MenuItem> varsayılan tema stili ile etkileşim. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Özelliği mantığını kullanır veri bağlama yerel olarak diğer durum özellik ve yöntem çağrıları çerçevesinde özelliği durumunu korumak için. Bağlanan başka bir örnek özellik <xref:System.Windows.Data.BindingMode.TwoWay> varsayılan olarak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

-   Özel bağımlılık özelliği özellik Devralmada ayarlayarak da etkinleştirebilirsiniz <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> bayrağı. Özellik devralma burada üst öğeler ve alt öğeleri bir özelliği ortak olan ve için alt öğeleri üst ayarlarken aynı değere ayarlamanız, belirli özellik değerine sahip olacak şekilde mantıklı bir senaryo için yararlıdır. Örnek özellik devralınamaz <xref:System.Windows.FrameworkElement.DataContext%2A>, önemli bir ana öğe-ayrıntı senaryo verilerini sunumu için etkinleştirme işlemleri bağlama için kullanılır. Yaparak <xref:System.Windows.FrameworkElement.DataContext%2A> devralınabilir, herhangi bir alt öğe o veri bağlamı da devralır. Özellik değeri kalıtımı nedeniyle bir veri bağlamı sayfası veya uygulama kökü belirtebilirsiniz ve tüm olası alt öğeleri bağlamaları için belirtmek gerekmez. <xref:System.Windows.FrameworkElement.DataContext%2A> Ayrıca devralma varsayılan değerini geçersiz kılar, ancak bu her zaman yerel olarak herhangi bir belirli bir alt öğe üzerinde ayarlanabilir göstermek için iyi bir örnektir; Ayrıntılar için bkz [hiyerarşik veriler ile ana öğe-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Özellik değeri kalıtımı olası performans maliyetine sahip ve bu nedenle kaçınılmalıdır; Ayrıntılar için bkz [özellik değeri kalıtımı](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

-   Ayarlama <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> , bağımlılık özelliği algılandı veya gezinti günlük kaydı hizmetleri tarafından kullanılan belirten bayrak. Örneğidir <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> özelliği; herhangi bir öğeyi bir seçim Seçili denetim kalıcı günlüğe kaydetme geçmişini çıkıldığında olduğunda.

<a name="RODP"></a>
## <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri

Salt okunur bağımlılık özelliği tanımlayabilirsiniz. Ancak, kimlik doğrulamasıyla açığa çıkaran ve bunları özellik sistemi ile kaydetme yordamını olduğu gibi salt okunur olarak özelliğinizi neden tanımlayabilir senaryoları biraz farklı olabilir. Daha fazla bilgi için [salt okunur bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).

<a name="CTDP"></a>
## <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri

Koleksiyon türü bağımlılık özellikleri dikkate alınması gereken bazı ek uygulama sorunlarına sahip. Ayrıntılar için bkz [koleksiyon türü bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md).

<a name="SecurityC"></a>
## <a name="dependency-property-security-considerations"></a>Bağımlılık özelliği güvenlik konuları

Bağımlılık özellikleri ortak özellik olarak bildirilmelidir. Bağımlılık özelliği tanımlayıcı alanlarını, genel statik alanlar bildirilmelidir. (Korumalı gibi) diğer erişim düzeyleri bildirme girişimi olsa bile, bir bağımlılık özelliği her zaman özellik sistemi ile birlikte tanımlayıcısı aracılığıyla erişilebilir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Korumalı tanımlayıcı alan meta verileri raporlama ya da değer belirleme nedeniyle potansiyel olarak erişilebilir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] gibi özellik sistemi parçası olan <xref:System.Windows.LocalValueEnumerator>. Daha fazla bilgi için [bağımlılık özelliği güvenliği](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

<a name="DPCtor"></a>
## <a name="dependency-properties-and-class-constructors"></a>Bağımlılık özellikleri ve sınıf oluşturucuları

Genel bir sınıf oluşturucuları (genellikle FxCop gibi kod çözümleme araçları tarafından zorunlu tutulur) yönetilen kod programlama İlkesi sanal yöntemleri çağırmamalıdır yoktur. Bu temel bir türetilen sınıf oluşturucusu başlatma oluşturucular çağrılabilir ve Oluşturucusu aracılığıyla sanal yöntemin girilmesinin yapılandırılmakta nesne örneğinin bir tam başlatma durumunda oluşabilecek olmasıdır. Zaten türetilen herhangi bir sınıftan türetilen zaman <xref:System.Windows.DependencyObject>, özellik sistemi çağırır ve sanal yöntemleri dahili olarak sunan farkında olmalıdır. Bu sanal yöntemler parçası olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği Sistem Hizmetleri. Yöntemleri geçersiz kılma değeri belirleme katılmak türetilmiş sınıfları sağlar. Belirli bir oluşturucu desenler izleyen sürece çalışma zamanı başlatma ile ilgili olası sorunları önlemek için bağımlılık özellik değerleri, sınıfların oluşturuculardan ayarlanmamalıdır. Ayrıntılar için bkz [DependencyObjects için güvenli Oluşturucu desenleri](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
- [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
- [Koleksiyon Türü Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)
- [Bağımlılık Özelliği Güvenliği](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
- [XAML Yükleme ve Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
- [DependencyObjects için Güvenli Oluşturucu Desenleri](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)