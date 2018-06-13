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
ms.openlocfilehash: 2623f34418aad7a0b29c52d1310fdc79afced790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541969"
---
# <a name="custom-dependency-properties"></a>Özel Bağımlılık Özellikleri
Bu konuda nedenleri açıklanmaktadır, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama geliştiricileri ve bileşen yazarlar özel bağımlılık özelliği oluşturmak isteyebilirsiniz ve performansı iyileştirmek bazı uygulama seçenekleri yanı sıra uygulama adımlarını açıklar Kullanılabilirlik veya çok yönlülük özelliğinin.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu bağımlılık özellikleri varolan bağımlılık özelliklerinin tüketicisi açısından anladığınızı varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) konu. Bu konudaki örnekleri takip etmek için ayrıca anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="whatis"></a>   
## <a name="what-is-a-dependency-property"></a>Bağımlılık özelliği nedir?  
 Aksi takdirde ne olacağını etkinleştirebilirsiniz bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bağımlılık özelliği olarak uygulayarak stil, veri bağlama, devralma, animasyonları ve varsayılan değerleri desteklemek için özelliği. Bağımlılık özellikleri ile kayıtlı özelliklerdir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çağırarak özellik sistemi <xref:System.Windows.DependencyProperty.Register%2A> yöntemi (veya <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), ve tarafından yedeklenen bir <xref:System.Windows.DependencyProperty> tanımlayıcı alanı. Bağımlılık özellikleri yalnızca kullanılabilir <xref:System.Windows.DependencyObject> türleri, ancak <xref:System.Windows.DependencyObject> oldukça yüksek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğunu bulunan sınıflar için sınıf hiyerarşisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri destekleyebilir. Bağımlılık özellikleri ve bazı terminoloji ve bunları bu tanımlamak için kullanılan kuralları hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="example_dp"></a>   
## <a name="examples-of-dependency-properties"></a>Bağımlılık özellikleri örnekleri  
 Örnekler üzerinde uygulanan bağımlılık özelliklerinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları içerir <xref:System.Windows.Controls.Control.Background%2A> özelliği, <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve <xref:System.Windows.Controls.TextBox.Text%2A> arasında diğer birçok özellik. Bir sınıf tarafından kullanıma sunulan her bağımlılık özelliği karşılık gelen bir public static alanı türü sahip <xref:System.Windows.DependencyProperty> o aynı sınıf içinde sunulan. Bu bağımlılık özelliği için tanımlayıcısıdır. Bir kural kullanılarak tanımlayıcı adlı: dizesiyle bağımlılık özelliğinin adı `Property` eklenmiş. Örneğin, karşılık gelen <xref:System.Windows.DependencyProperty> için tanımlayıcı alanı <xref:System.Windows.Controls.Control.Background%2A> özelliği <xref:System.Windows.Controls.Control.BackgroundProperty>. Kayıtlı olduğu ve tanımlayıcı ardından daha sonra arama gibi bağımlılık özelliği ile ilgili diğer işlemleri için kullanılan tanımlayıcı bağımlılık özelliği hakkında bilgi depolar <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
 Bölümünde belirtildiği gibi [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md), tüm bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (en ekli dışında) özelliklerdir de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" uygulama nedeniyle özellikleri. Bu nedenle, kodundan alabilir veya çağırarak bağımlılık özelliklerini ayarlama [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] diğer kullanacağınız aynı şekilde sarmalayıcıları tanımlamak erişimciler [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri. Oluşturulan bağımlılık özellikleri tüketici olarak, genellikle kullanmaz <xref:System.Windows.DependencyObject> yöntemleri <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A>, temel alınan özellik sistemi bağlantı noktası olan. Bunun yerine, mevcut uyarlamasını [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri zaten olarak adlandırılan <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> içinde `get` ve `set` tanımlayıcı alanı uygun şekilde kullanarak özelliğinin kapsayıcı uygulamaları . Özel bir bağımlılık özelliği kendiniz uyguluyorsanız, benzer şekilde sarmalayıcı tanımlama.  
  
<a name="backing_with_dp"></a>   
## <a name="when-should-you-implement-a-dependency-property"></a>Ne zaman bir bağımlılık özelliği uygulamanız gerekir?  
 Ne zaman uygulamanız bir özelliği bir sınıf üzerinde sınıfınız türetilen sürece <xref:System.Windows.DependencyObject>, özelliği ile geri seçeneğine sahip bir <xref:System.Windows.DependencyProperty> tanımlayıcısı ve bu nedenle bir bağımlılık özelliği yapmak için. Bağımlılık özelliği, özelliğine sahip her zaman gerekli veya uygun değildir ve senaryo gereksinimlerinize göre değişir. Bazı durumlarda, özel bir alanla özelliğinizi yedekleme tipik tekniği yeterlidir. Bir veya daha fazlasını desteklemek için özelliği istediğiniz zaman ancak, siz özelliğinizi bağımlılık özelliği olarak uygulamalıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri:  
  
-   Özelliğinizi stilde ayarlanabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
-   Veri bağlama desteklemek için özelliği istiyor. Veri bağlama bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [özellikleri, iki denetimler bağlama](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).  
  
-   Özelliğinizi dinamik kaynak başvurusuyla ayarlanabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Bir özellik değeri otomatik olarak öğe ağacındaki bir üst öğeden devralınacak şekilde istiyor. Bu durumda, kaydetme <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi için özellik sarmalayıcı oluşturabilir olsa bile [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] erişim. Daha fazla bilgi için bkz: [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Özelliğinizi canlandırılabilir olmasını istiyorsunuz. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Özelliğin önceki değeri özellik sistem, ortamı veya kullanıcı tarafından ya da okuma ve stiller kullanılarak gerçekleştirilen işlemler tarafından değiştirildi rapor özelliği sisteme istediğinizde. Özellik meta verileri kullanarak, özellik, özellik değeri tam olarak değiştirildi özellik sistemi belirler her zaman çağrılan bir geri çağırma yöntemi belirtebilirsiniz. Özellik değeri zorlama buna ilgili bir kavramdır. Daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Tarafından da kullanılan kurulan meta veri kuralları kullanmak istediğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir özellik değerini değiştirme görsel bir öğe için yeniden oluşturmak için Düzen sistemi ihtiyaç duyması durumunda olup olmadığını raporlama gibi işlemler. Veya türetilmiş sınıflar varsayılan değeri gibi meta veri tabanlı özellikleri değiştirebilirsiniz meta verileri geçersiz kılmaları kullanılacak kullanabilmek ister.  
  
-   Almak için özel bir denetim özelliklerini istediğiniz [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] desteği, gibi **özellikleri** penceresi düzenleme. Daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Bu senaryolar incelediğinizde, senaryonuz var olan bir bağımlılık özelliğinin meta verileri geçersiz kılma yerine tarafından tamamen yeni bir özellik uygulama elde edebilirsiniz olup olmadığını de dikkate almalısınız. Meta veriler geçersiz kılma pratik olup senaryonuza ve bu senaryo mevcut olan uygulama ne kadar yakından benzer bağlıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özellikleri ve sınıfları. Var olan özellikleri meta verileri geçersiz kılma hakkında daha fazla bilgi için bkz: [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="checklist"></a>   
## <a name="checklist-for-defining-a-dependency-property"></a>Bağımlılık özelliği tanımlamak için Denetim listesi  
 Bağımlılık özelliği tanımlama dört ayrı kavramlarını oluşur. Bu kavramlar bunlardan bazıları tek satırlık bir uygulama kodunda olarak birleştirilen sonlandırmak için mutlaka katı yordamsal adımlar değildir:  
  
-   (İsteğe bağlı) Bağımlılık özelliği için özellik meta verileri oluşturun.  
  
-   Özellik adı belirtme sahip türü ve özellik değeri türü özellik sistemi ile kaydedin. Ayrıca özellik meta verileri kullandıysanız belirtin.  
  
-   Tanımlayan bir <xref:System.Windows.DependencyProperty> tanımlayıcı olarak bir `public` `static` `readonly` sahibi türündeki alan.  
  
-   Tanımlayan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" özelliği adıyla eşleşen bir bağımlılık özelliğinin adı. Uygulama [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "sarmalayıcı" özelliğin `get` ve `set` onu yedekleyen bağımlılık özelliği ile bağlanmak için erişimcileri.  
  
<a name="registering"></a>   
### <a name="registering-the-property-with-the-property-system"></a>Özelliğin özellik sistemi ile kaydetme  
 Bağımlılık özelliği olarak, bir özellik için sırayla bu özellik özellik sistemi tarafından korunan bir tabloya kaydetmek ve niteleyici olarak sonraki özelliği sistem işlemleri için kullanılan benzersiz bir tanımlayıcı vermek gerekir. Bu işlemler dahili işlemlerin olması ya da özellik sistemi çağırma kendi kodunuzu olabilir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Özellik kaydetmek için arama <xref:System.Windows.DependencyProperty.Register%2A> sınıfınız (sınıf içinde ancak hiçbir üye tanımları dışında) gövdesi içinde yöntemi. Tanımlayıcı alanı de tarafından sağlanan <xref:System.Windows.DependencyProperty.Register%2A> dönüş değeri olarak yöntem çağrısı. Nedeni, <xref:System.Windows.DependencyProperty.Register%2A> çağrı yapılır dışında tanımları diğer üyesidir atayın ve oluşturmak için bu dönüş değeri kullandığından bir `public` `static` `readonly` türü alan <xref:System.Windows.DependencyProperty> sınıfınız bir parçası olarak. Bu alan, bağımlılık özelliği tanımlayıcı olur.  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### <a name="dependency-property-name-conventions"></a>Bağımlılık özelliği adı kuralları  
 Tüm ancak olağanüstü durumlarda izlemelisiniz bağımlılık özellikleri ile ilgili yerleşik adlandırma kuralları vardır.  
  
 Bağımlılık özelliği ilk parametresi olarak verilen bu örnekte olduğu gibi "AquariumGraphic" temel bir adı vardır <xref:System.Windows.DependencyProperty.Register%2A>. Bu ad her kayıt türü içinde benzersiz olmalıdır. Taban türleri aracılığıyla devralınan bağımlılık özellikleri zaten kayıt türü bir parçası olarak kabul edilir; devralınan özellik adlarını yeniden kaydedilemedi. Ancak, bile bu bağımlılık özelliği olmayan devralındığında bağımlılık özelliği sahibi olarak bir sınıf eklemek için bir yöntem yoktur; Ayrıntılar için bkz [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Tanımlayıcı alanı oluşturduğunuzda, artı soneki kayıtlı olarak bu alan özellik adıyla ad `Property`. Bu alan, bağımlılık özelliği tanımlayıcısıdır ve daha sonra için bir giriş olarak kullanılacak <xref:System.Windows.DependencyObject.SetValue%2A> ve <xref:System.Windows.DependencyObject.GetValue%2A> yaptığınız tüm diğer kod erişim tarafından kendi kodunuzu özelliğiyle herhangi bir harici kod erişim tarafından sarmalayıcıları içinde çağrılarına izin vermek , özellik sistemi tarafından ve potansiyel olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci.  
  
> [!NOTE]
>  Bağımlılık özelliği sınıfı gövdesinde tanımlama tipik uygulamasıdır, ancak bir bağımlılık özelliği sınıfı statik oluşturucuda tanımlamak da mümkündür. Bağımlılık özelliği başlatmak için kod birden fazla satır ihtiyacınız varsa bu yaklaşımı mantıklı olabilir.  
  
<a name="wrapper1"></a>   
### <a name="implementing-the-wrapper"></a>"Sarmalayıcı" uygulama  
 Sarmalayıcı uygulamanızı çağırmalıdır <xref:System.Windows.DependencyObject.GetValue%2A> içinde `get` uygulaması, ve <xref:System.Windows.DependencyObject.SetValue%2A> içinde `set` uygulaması (özgün kayıt çağrısı ve alan burada gösterilen çok daha anlaşılır olması için).  
  
 Tüm ancak olağanüstü durumlarda, kapsayıcı uygulamaları yalnızca gerçekleştirmesi gereken <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> Eylemler, sırasıyla. Bunun nedeni konuda tartışılan [XAML yükleme ve bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
 Üzerinde sağlanan tüm var olan ortak bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağımlılık özelliklerinin nasıl çalıştığını karmaşıklığını çoğunu ya da kendiliğinden özellik sistemi davranışını ya da sınıflar bu basit sarmalayıcı uygulama modeli kullanın; zorlama veya özellik değiştirme geri çağırmalar aracılığıyla özellik meta verileri gibi diğer kavramlar uygulanır.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 Kurala göre sarmalayıcı özelliğinin adı seçilen ve ilk parametresi olarak belirtilen ad aynı yeniden olmalıdır <xref:System.Windows.DependencyProperty.Register%2A> özellik kayıtlı arama. Özelliğinizi kuralı izlemiyorsa bu mutlaka tüm olası kullanır devre dışı değildir, ancak birkaç önem düzeyindeki sorunlar karşılaşır:  
  
-   Stilleri ve şablonları belirli yönlerini çalışmaz.  
  
-   Çoğu araçları ve tasarımcıları düzgün serileştirmek için adlandırma kuralları kullanır gerekir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veya bir özelliğe düzeyinde Tasarımcı ortamı Yardım sağlamak için.  
  
-   Geçerli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleyicisi sarmalayıcıları tamamen atladığından ve öznitelik değerlerini işlerken adlandırma kuralına kullanır. Daha fazla bilgi için bkz: [XAML yükleme ve bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
<a name="metadata"></a>   
### <a name="property-metadata-for-a-new-dependency-property"></a>Yeni bir bağımlılık özelliği için özellik meta verileri  
 Bağımlılık özelliği kaydettiğinizde, kayıt özellik sistemi aracılığıyla özelliği özellikleriyle depolayan bir meta veri nesnesi oluşturur. Bu özelliklerin çoğu özelliği ile basit imzalarını kayıtlı değilse, ayarlanan Varsayılanları sahip <xref:System.Windows.DependencyProperty.Register%2A>. Diğer imzalarını <xref:System.Windows.DependencyProperty.Register%2A> özelliği kaydettiğiniz istediğiniz meta veriler belirtmenizi sağlar. Bağımlılık özellikleri için verilen yaygın meta verileri, bunları özelliği kullanan yeni örneklerinde uygulanan varsayılan bir değer vermektir.  
  
 Türetilmiş bir sınıf mevcut bir bağımlılık özelliği oluşturuyorsanız <xref:System.Windows.FrameworkElement>, daha özel meta veri sınıfını kullanabilirsiniz <xref:System.Windows.FrameworkPropertyMetadata> temel yerine <xref:System.Windows.PropertyMetadata> sınıfı. Oluşturucusu <xref:System.Windows.FrameworkPropertyMetadata> sınıfı birlikte çeşitli meta verilerin özellikleri belirtebileceğiniz çeşitli imzaları sahiptir. Yalnızca varsayılan değeri belirtmek istiyorsanız, tek bir parametre türü alır imza kullanmak <xref:System.Object>. Bu nesne parametresi, bir özellik için türe özgü varsayılan değer olarak geçirin (sağlanan varsayılan değeri olarak sağlanan türü olmalıdır `propertyType` parametresinde <xref:System.Windows.DependencyProperty.Register%2A> çağrısı).  
  
 İçin <xref:System.Windows.FrameworkPropertyMetadata>, özellik için meta veri seçeneği bayrakları de belirtebilirsiniz. Bu bayrakların özellik meta verileri ayrık özelliklerindeki halinde kayıttan sonra dönüştürülür ve belirli koşulları yerleşim altyapısı gibi başka bir işlem için iletişim kurmak için kullanılır.  
  
#### <a name="setting-appropriate-metadata-flags"></a>Uygun meta verileri bayrakları ayarlama  
  
-   Özellik (veya değişiklikleri değeri) etkileyip etkilemediğini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], düzen sistemi boyutu veya bir sayfasında, öğe işleme nasıl özellikle etkiler bir veya daha fazla aşağıdaki bayraklar ayarlayın: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> Bu özellik için bir değişiklik değişiklik gerektirdiğini gösterir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] burada içeren nesne gerektirebilecek fazla veya az alanı üst içinde işleme. Örneğin, "Genişliği" özelliği bu bayrağı ayarlanmış olmalıdır.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> Bu özellik için bir değişiklik değişiklik gerektirdiğini gösterir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] genellikle işleme ayrılmış alanı bir değişiklik gerektirmez, ancak alanı içinde konumlandırma değiştiğini anlamına gelmez. Örneğin, bir "Hizalama" özelliği bu bayrağı ayarlanmış olmalıdır.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> gösteren başka bir değişiklik oluştuğunu düzeni ve ölçü etkilemez, ancak başka bir işleme gerektirir. Bir örnek, "Arka plan" gibi varolan bir öğenin rengi değişir bir özellik olabilir.  
  
    -   Bu bayrakların genellikle meta verilerindeki bir protokol olarak özelliği sistem veya düzenini geri aramalar kendi geçersiz kılma uygulamalar için kullanılır. Örneğin, olabilir bir <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> çağıracak geri çağırma <xref:System.Windows.UIElement.InvalidateArrange%2A> örneğinin herhangi bir özelliği bir değer değişiklik raporları ve sahip <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> olarak `true` meta.  
  
-   Bazı özellikler işleme özelliklerini içeren üst öğenin yukarıda belirtilen gereken boyut değişiklikleri özellik şekillerde etkileyebilir. Örnek <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> değişiklikler bu özelliğe genel işleme paragraf içeren akış belgenin burada değiştirebilirsiniz akış belge modelinde kullanılan özelliği. Kullanım <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> veya <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> kendi özelliklerinizi benzer durumlarda tanımlamak için.  
  
-   Varsayılan olarak, bağımlılık özellikleri veri bağlamayı destekler. Kasıtlı olarak durumlarda veri bağlama veri bağlama için gerçekçi hiçbir senaryo olduğu veya veri bağlaması büyük nesne için Performans sorun olarak kabul edilen devre dışı bırakabilirsiniz.  
  
-   Varsayılan olarak, veri bağlama <xref:System.Windows.Data.Binding.Mode%2A> bağımlılık özellikleri varsayılanlara için <xref:System.Windows.Data.BindingMode.OneWay>. Bağlamanın olması için her zaman değiştirebilirsiniz <xref:System.Windows.Data.BindingMode.TwoWay> bağlama örneği başına; Ayrıntılar için bkz: [bağlama yönünü belirtmek](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md). Ancak Kullan özelliği yapmayı seçebilirsiniz bağımlılık özelliği yazarı olarak <xref:System.Windows.Data.BindingMode.TwoWay> varsayılan bağlama modu. Varolan bir bağımlılık özelliğinin örneğidir <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; bu özellik için bir senaryodur <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> mantığı ve birleştirme, ayarı <xref:System.Windows.Controls.MenuItem> varsayılan tema stili ile etkileşim. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Özelliği mantığı kullanan veri bağlama yerel diğer durumu özellikleri ve yöntem çağrıları için uygun özelliği durumunu korumak için. Bağlar başka bir örnek özellik <xref:System.Windows.Data.BindingMode.TwoWay> varsayılan olarak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.  
  
-   Özellik devralma özel bir bağımlılık özelliği olarak ayarlayarak etkinleştirebilirsiniz <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> bayrağı. Özellik devralma burada üst öğeler ve alt öğelerini bir özellik genelde sahip ve için alt öğeler üst ayarlarken aynı değere ayarlar, belirli özellik değerine sahip olacak şekilde mantıklıdır bir senaryo için yararlıdır. Bir örnek devralınabilir özelliği <xref:System.Windows.FrameworkElement.DataContext%2A>, hangi veri sunum önemli ana-ayrıntı senaryosu etkinleştirme işlemleri bağlama için kullanılır. Yaparak <xref:System.Windows.FrameworkElement.DataContext%2A> devralınabilir, herhangi bir alt öğe, veri bağlamı da devralır. Özellik değeri devralma nedeniyle sayfa veya uygulama kökünde bir veri bağlamı belirtebilirsiniz ve tüm olası alt öğelerindeki bağlamaları için belirtmek gerekmez. <xref:System.Windows.FrameworkElement.DataContext%2A> Ayrıca devralma varsayılan değerini geçersiz kılar, ancak bu her zaman yerel olarak herhangi bir belirli alt öğede ayarlanabilir göstermek için iyi bir örnektir; Ayrıntılar için bkz [hiyerarşik veriler ile ana-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Özellik değeri devralma olası bir performans maliyetiyle sahip ve bu nedenle kullanılmamalıdır; Ayrıntılar için bkz [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Ayarlama <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> bağımlılık özelliği algılandı veya gezinti günlük kaydı hizmetleri tarafından kullanılan olmadığını göstermek için bayrak. Örnek <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> özellik; bir seçimi seçili herhangi bir öğeyi denetim kalıcı hale günlük kaydı geçmiş gittiğinizde olduğunda.  
  
<a name="RODP"></a>   
## <a name="read-only-dependency-properties"></a>Salt Okunur Bağımlılık Özellikleri  
 Salt okunur bir bağımlılık özelliği tanımlayabilirsiniz. Ancak, özellik sistemi ile kaydetme ve tanımlayıcı gösterme yordamı olduğu gibi salt okunur olarak özelliğinizi neden tanımlayabilir senaryoları biraz farklı olabilir. Daha fazla bilgi için bkz: [salt okunur bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
<a name="CTDP"></a>   
## <a name="collection-type-dependency-properties"></a>Koleksiyon Türü Bağımlılık Özellikleri  
 Koleksiyon türü bağımlılık özellikleri dikkate alınması gereken bazı ek uygulama sorunlarına sahip. Ayrıntılar için bkz [koleksiyon türü bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md).  
  
<a name="SecurityC"></a>   
## <a name="dependency-property-security-considerations"></a>Bağımlılık özelliği güvenlik konuları  
 Bağımlılık özellikleri ortak özellikleri olarak bildirilmelidir. Bağımlılık özelliği tanımlayıcı alanlarını ortak statik alanları olarak bildirilmelidir. (Korumalı gibi) diğer erişim düzeyleri bildirme girişiminde bulunursanız, bağımlılık özelliği her zaman tanımlayıcı özellik sistemi ile birlikte aracılığıyla erişilebilir [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Korumalı tanımlayıcı alanı meta verileri raporlama ya da değer belirlemeyi nedeniyle potansiyel olarak erişilebilen [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] gibi özellik sisteminin parçası olan <xref:System.Windows.LocalValueEnumerator>. Daha fazla bilgi için bkz: [bağımlılık özelliği güvenlik](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
<a name="DPCtor"></a>   
## <a name="dependency-properties-and-class-constructors"></a>Bağımlılık özellikleri ve sınıf oluşturucuları  
 Oluşturucular sınıfı (genellikle FxCop gibi kod çözümleme araçları tarafından zorunlu tutulur) yönetilen kod programlama genel bir ilkesi çağrılmayan sanal yöntemler vardır. Bu temel bir türetilmiş sınıf oluşturucu başlatma oluşturucular çağrılabilir ve Oluşturucusu üzerinden sanal yöntemi girme yapılandırılan bir nesne örneğinin tamamlanmamış başlatma durumu sırasında oluşabilecek kaynaklanır. Zaten türetilen herhangi bir sınıftan türetilen zaman <xref:System.Windows.DependencyObject>, özellik sistemi çağırır ve sanal yöntemler dahili kullanıma sunan bilincinde olmanız gerekir. Bu sanal yöntemler parçası olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği Sistem Hizmetleri. Yöntemleri geçersiz kılma değeri belirleme katılmak türetilen sınıflar sağlar. Belirli Oluşturucusu desenler izleyen sürece çalışma zamanı başlatma olası sorunları önlemek için bağımlılık özellik değerleri, sınıfların oluşturuculardan ayarlamanız gerekir değil. Ayrıntılar için bkz [DependencyObjects için güvenli oluşturucu desenler](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Koleksiyon Türü Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Bağımlılık Özelliği Güvenliği](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [XAML Yükleme ve Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)  
 [DependencyObjects için Güvenli Oluşturucu Desenleri](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
