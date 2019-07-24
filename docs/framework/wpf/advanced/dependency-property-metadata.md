---
title: Bağımlılık Özelliği Meta Verisi
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 800bf80e5ba3e697c122bcf4b1bc0f302357d087
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401619"
---
# <a name="dependency-property-metadata"></a>Bağımlılık Özelliği Meta Verisi
Özellik [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistemi, yansıma veya genel ortak dil çalışma zamanı (CLR) özellikleri aracılığıyla bir özellik hakkında rapor edilenden daha fazla geçen bir meta veri raporlama sistemi içerir. Bağımlılık özelliği için meta veriler ayrıca bir bağımlılık özelliğini tanımlayan sınıf tarafından benzersiz bir şekilde atanabilir, Dependency özelliği farklı bir sınıfa eklendiğinde değiştirilebilir ve özel olarak tanımlayan Taban sınıftan bağımlılık özelliği.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığında bağımlılık özelliklerini, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarda var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)konusunu okuduğunuzu varsaymaktadır. Bu konudaki örnekleri izlemek için, uygulamaların nasıl yazılacağını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de anlamanız ve bilmeniz gerekir.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Bağımlılık özelliği meta verileri nasıl kullanılır  
 Bağımlılık özelliği meta verileri, bir bağımlılık özelliğinin özelliklerini incelemek için sorgulanabilen bir nesne olarak mevcuttur. Bu meta verilere, tüm verilen bağımlılık özelliğini işlerken de genellikle özellik sistemi tarafından erişilir. Bağımlılık özelliği için meta veri nesnesi aşağıdaki bilgi türlerini içerebilir:  
  
- Bağımlılık özelliği için yerel değer, stil, devralma vb. tarafından başka bir değer belirlenemiyorsa, bağımlılık özelliği için varsayılan değer. Varsayılan değerlerin, bağımlılık özelliklerine değer atarken özellik sistemi tarafından kullanılan önceliğe nasıl katılacağı hakkında ayrıntılı bir tartışma için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
- Sahip türü temelinde zorlama veya değişiklik bildirimi davranışlarını etkileyen geri çağırma uygulamalarına başvurular. Bu geri çağırmaların genellikle özel bir erişim düzeyiyle tanımlandığını unutmayın. bu nedenle, başvurular izin verilen erişim kapsamınızda olduğundan meta verilerden gerçek başvuruları almak genellikle mümkün değildir. Bağımlılık özelliği geri çağırmaları hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md).  
  
- Söz konusu bağımlılık özelliği bir WPF framework düzeyi özelliği olarak kabul edildiğinde, meta veriler WPF framework düzeyi bağımlılık özelliği özelliklerini içerebilir, bu da WPF framework düzeyi gibi hizmetlerin bilgilerini ve durumunu rapor edebilir Düzen altyapısı ve özellik devralma mantığı. Bağımlılık özelliği meta verilerinin bu yönü hakkında daha fazla bilgi için bkz. [Framework özelliği meta verileri](framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Meta veri API 'Leri  
 Özellik sistemi <xref:System.Windows.PropertyMetadata> tarafından kullanılan meta veri bilgilerinin çoğunu raporlayan tür sınıftır. Bağımlılık özellikleri özellik sistemine kaydedildiğinde meta veri örnekleri isteğe bağlı olarak belirtilir ve kendilerini sahip olarak ekleyen ya da temel sınıf bağımlılığıyla devraldığı meta verileri geçersiz kılan ek türler için yeniden belirtilebilir özellik tanımı. (Bir özellik kaydının meta verileri belirtmediğinden, bu sınıf için varsayılan değerlerle <xref:System.Windows.PropertyMetadata> varsayılan değerleri oluşturulur.) Kayıtlı meta veriler, bir <xref:System.Windows.PropertyMetadata> <xref:System.Windows.DependencyObject> örnekteki bağımlılık özelliğinden meta veri alan <xref:System.Windows.DependencyProperty.GetMetadata%2A> çeşitli aşırı yüklemeleri çağırdığınızda olarak döndürülür.  
  
 Daha <xref:System.Windows.PropertyMetadata> sonra sınıf, WPF framework düzeyi sınıfları gibi mimari bölümlere daha özel meta veriler sağlamak için öğesinden türetilir. <xref:System.Windows.UIPropertyMetadata>animasyon raporlama ekler ve <xref:System.Windows.FrameworkPropertyMetadata> önceki bölümde belirtilen WPF framework düzeyi özelliklerini sağlar. Bağımlılık özellikleri kaydedildiğinde, bu <xref:System.Windows.PropertyMetadata> türetilmiş sınıflarla kaydedilebilir. Meta veriler incelenirse, daha belirli özellikleri <xref:System.Windows.PropertyMetadata> incelemenize olanak sağlamak için temel tür türetilmiş sınıflara dönüşebilir olabilir.  
  
> [!NOTE]
>  İçinde <xref:System.Windows.FrameworkPropertyMetadata> belirtime Özellik özellikleri bazen bu belgelerde "Flags" olarak adlandırılır. Bağımlılık özelliği kayıtlarında veya meta veri geçersiz Kılmalarda kullanılmak üzere yeni meta veri örnekleri oluşturduğunuzda, bu değerleri, flagwise sabit <xref:System.Windows.FrameworkPropertyMetadataOptions> listesini kullanarak belirtirsiniz ve sonra, numaralandırmanınbüyükolasılıklabirleştirilmişdeğerlerini<xref:System.Windows.FrameworkPropertyMetadata> Oluşturucu. Ancak, oluşturulduktan sonra, bu seçenek özellikleri bir dizi içinde, <xref:System.Windows.FrameworkPropertyMetadata> numaralandırma değeri oluşturmak yerine bir dizi Boole özelliği olarak sunulur. Boolean özellikleri, ilgilendiğiniz bilgileri almak için bir flagwise numaralandırma değerine bir maske uygulamanızı gerektirmek yerine her bir koşula göz atamamanızı sağlar. Oluşturucu, Oluşturucu imzasının uzunluğunu <xref:System.Windows.FrameworkPropertyMetadataOptions> makul bir şekilde tutmak için birleştirilmiş ' i kullanır, ancak gerçek oluşturulmuş meta veriler, meta verilerin sorgulanmasını daha sezgisel hale getirmek için ayrık özellikler sunar.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Meta verilerin geçersiz kılınması, ne zaman bir sınıf türetileceğini  
 Özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistemi, bağımlılık özelliklerinin bazı özelliklerini tamamen yeniden uygulanması gerekmeden değiştirmek için yetenekler kurdu. Bu, belirli bir tür üzerinde mevcut olduğundan, bağımlılık özelliği için farklı bir özellik meta verisi oluşturarak yapılır. Mevcut bağımlılık özelliklerinin çoğu sanal özellik değildir; bu nedenle, devralınan sınıflarda "yeniden uygulama" özelliği yalnızca mevcut üyenin gölgelendirilir.  
  
 Bir tür üzerinde bir bağımlılık özelliği için etkinleştirmeye çalıştığınız senaryo mevcut bağımlılık özelliklerinin özellikleri değiştirilerek sağlanmazsa, bir türetilmiş sınıf oluşturmak ve ardından özel bir bağımlılık özelliği bildirmek için gerekli olabilir. Türetilmiş sınıfınız üzerinde. Özel bağımlılık özelliği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'ler tarafından tanımlanan bağımlılık özellikleriyle aynı şekilde davranır. Özel bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
 Geçersiz kılabileceğiniz bir bağımlılık özelliğinin bir önemli özelliği, değer türüdür. İhtiyaç duyduğunuz yaklaşık bir davranışın bulunduğu bir bağımlılık özelliğini devraldıysanız, ancak bunun için farklı bir tür isterseniz, özel bir bağımlılık özelliği uygulamanız gerekir, belki de tür dönüştürmesi veya diğer özellikler aracılığıyla özellikleri bağlayabilirsiniz Özel sınıfınıza uygulama. Ayrıca, bu geri çağırma, kendi <xref:System.Windows.ValidateValueCallback>meta verilerinde değil, kayıt alanında bulunduğundan, var olan bir başkasıyla değiştirilemez.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Mevcut meta verileri değiştirme senaryoları  
 Mevcut bir bağımlılık özelliğinin meta verileriyle çalışıyorsanız, bağımlılık özelliği meta verilerini değiştirmenin bir yaygın senaryosu varsayılan değeri değiştirmedir. Özellik sistemi geri çağırmaları değiştirme veya ekleme daha gelişmiş bir senaryodur. Türetilmiş bir sınıfın uygulamanız bağımlılık özellikleri arasında farklı ilişkiler içeriyorsa bunu yapmak isteyebilirsiniz. Hem kodu hem de bildirime dayalı kullanımı destekleyen bir programlama modeline sahip olmanın koşullarınız, özelliklerin herhangi bir sırada ayarlanmakta olması gerekir. Bu nedenle, herhangi bir bağımlı özellik bağlam olmadan tam zamanında ayarlanmalıdır ve bir Oluşturucu içinde bulunabilir gibi bir ayar sırasının farkında olamaz. Özellik sisteminin bu yönü hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](dependency-property-callbacks-and-validation.md). Doğrulama geri çağırmaları meta verilerin bir parçası değildir; bağımlılık özelliği tanımlayıcısının bir parçasıdır. Bu nedenle, meta veriler geçersiz kılınarak doğrulama geri çağırmaları değiştirilemez.  
  
 Bazı durumlarda, mevcut bağımlılık özelliklerindeki WPF framework düzeyi özelliği meta veri seçeneklerini de değiştirmek isteyebilirsiniz. Bu seçenekler, WPF framework düzeyi özellikleriyle ilgili bazı bilinen koşulları, Düzen sistemi gibi diğer WPF framework düzeyi süreçleriyle iletişim kurar.  Seçeneklerin ayarlanması genellikle yeni bir bağımlılık özelliği kaydedilirken yapılır, ancak WPF framework düzeyi özellik meta verilerini bir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> veya <xref:System.Windows.DependencyProperty.AddOwner%2A> çağrısının parçası olarak değiştirmek de mümkündür. Kullanılacak belirli değerler ve daha fazla bilgi için bkz. [Framework özelliği meta verileri](framework-property-metadata.md). Yeni kaydedilmiş bir bağımlılık özelliği için bu seçeneklerin nasıl ayarlanması gerektiği hakkında daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Meta verileri geçersiz kılma  
 Meta verileri geçersiz kılma amacı, birincil olarak, sizin tipinizdeki mevcut olduğu gibi bağımlılık özelliğine uygulanan çeşitli meta veri türetilmiş davranışları değiştirme fırsatına sahip olur. Bunun nedenleri [meta veriler](#dp_metadata_contents) bölümünde daha ayrıntılı olarak açıklanmıştır. Bazı kod örnekleri dahil daha fazla bilgi için bkz. [bir bağımlılık özelliği Için meta verileri geçersiz kılma](how-to-override-metadata-for-a-dependency-property.md).  
  
 Kayıt çağrısı (<xref:System.Windows.DependencyProperty.Register%2A>) sırasında bağımlılık özelliği için özellik meta verileri sağlanabilir. Ancak çoğu durumda, bu bağımlılık özelliğini devraldığında sınıfınız için türe özgü meta veriler sağlamak isteyebilirsiniz. Bunu <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemini çağırarak yapabilirsiniz.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'lerden bir örnek için <xref:System.Windows.FrameworkElement> , sınıfı ilk olarak <xref:System.Windows.UIElement.Focusable%2A> bağımlılık özelliğini kaydeden türdür. Ancak sınıfı, bağımlılık özelliği için meta verileri geçersiz kılar, kendi başlangıç varsayılan değerini sağlar, öğesini `false` ile olarak `true`değiştirir ve aksi takdirde özgün <xref:System.Windows.UIElement.Focusable%2A> uygulamayı yeniden kullanır. <xref:System.Windows.Controls.Control>  
  
 Meta verileri geçersiz kıldığınızda, farklı meta veri özellikleri birleştirilir veya değiştirilmez.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>birleştirilir. Yeni <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>bir eklerseniz, bu geri çağırma meta verilerde depolanır. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değeri meta verilerde belirtilen en yakın üst öğesinden bir başvuru olarak yükseltilir.  
  
- İçin <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> gerçek özellik sistemi davranışı, hiyerarşideki tüm meta veri sahipleri için olan uygulamalar, özellik sistemi tarafından yürütme sırası, ilk olarak en fazla türetilen sınıfın geri çağırmaları çağrılır.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>değiştirilmiştir. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.DefaultValue%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değeri meta verilerde belirtilen en yakın üst öğesinden gelir.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>uygulamalar değiştirilmiştir. Yeni <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>bir eklerseniz, bu geri çağırma meta verilerde depolanır. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değeri meta verilerde belirtilen en yakın üst öğesinden bir başvuru olarak yükseltilir.  
  
- Özellik sistemi davranışı yalnızca <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> en anlık meta verilerde çağrılır. Hiyerarşideki diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamalar için başvuru korunmaz.  
  
 Bu davranış tarafından <xref:System.Windows.PropertyMetadata.Merge%2A>uygulanır ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
#### <a name="overriding-attached-property-metadata"></a>Ekli Özellik meta verilerini geçersiz kılma  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekli özellikler bağımlılık özellikleri olarak uygulanır. Bu, bağımsız sınıfların geçersiz kılabileceği özellik meta verilerine de sahip oldukları anlamına gelir. İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iliştirilmiş bir özelliğin kapsam değerlendirmeleri, genellikle herhangi birinin <xref:System.Windows.DependencyObject> üzerinde ayarlanmış bir iliştirilmiş özelliği olabilir. Bu nedenle, <xref:System.Windows.DependencyObject> herhangi bir türetilmiş sınıf herhangi bir iliştirilmiş özelliği için meta verileri geçersiz kılabilir, çünkü sınıfının bir örneğinde ayarlanmayabilir. Varsayılan değerleri, geri çağırmaları veya WPF framework düzeyi özelliği raporlama özelliklerini geçersiz kılabilirsiniz. Eğer iliştirilmiş özelliği sınıfınızın bir örneği üzerinde ayarlandıysa, bu geçersiz kılma özelliği meta veri özellikleri geçerlidir. Örneğin, varsayılan değeri geçersiz kılabilirsiniz; Örneğin, geçersiz kılma değeri, sınıfınızın örneklerine iliştirilmiş özelliğin değeri olarak raporlanır, ancak özellik başka bir şekilde ayarlanmamışsa.  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Özelliği iliştirilmiş özelliklerle ilgili değildir.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Mevcut bir bağımlılık özelliğinin sahibi olarak bir sınıf ekleme  
 Bir sınıf, <xref:System.Windows.DependencyProperty.AddOwner%2A> yöntemini kullanarak kendisini zaten kayıtlı olan bir bağımlılık özelliğinin sahibi olarak ekleyebilir. Bu, sınıfın, özgün olarak farklı bir tür için kaydedilmiş bir bağımlılık özelliği kullanmasına olanak sağlar. Ekleme sınıfı tipik olarak, önce bağımlılık özelliğini Owner olarak kaydetmiş olan türün türetilmiş bir sınıfı değildir. Bu, sınıfınızın ve türetilmiş sınıflarının orijinal sahip sınıfı olmadan bir bağımlılık özelliği uygulamasını ve aynı gerçek sınıf hiyerarşisinde ekleme sınıfını "devralmasını" sağlar. Ayrıca, ekleme sınıfı (ve tüm türetilmiş sınıflar de), özgün bağımlılık özelliği için türe özgü meta veriler sağlayabilir.  
  
 Özellik sistemi yardımcı programı yöntemleriyle kendisini sahip olarak eklemek için, ekleme sınıfı, özellik sisteminde her iki koda ve biçimlendirmeye maruz geçen tam bir katılımcı olmak üzere kendi üzerinde ek genel Üyeler bildirmelidir . Var olan bir bağımlılık özelliği ekleyen bir sınıf, bu bağımlılık özelliği için nesne modelini ortaya çıkaran ve yeni bir özel bağımlılık özelliğini tanımlayan bir sınıf gibi aynı sorumluluklara sahiptir. Kullanıma sunulacak ilk üye, bir bağımlılık özelliği tanımlayıcı alanıdır. Bu alan, `public static readonly` <xref:System.Windows.DependencyProperty.AddOwner%2A> çağrının dönüş değerine atanan türünde <xref:System.Windows.DependencyProperty>bir alan olmalıdır. Tanımlanacak ikinci üye, ortak dil çalışma zamanı (CLR) "sarmalayıcı" özelliğidir. Sarmalayıcı, kod içinde bağımlılık özelliğini daha kolay bir şekilde işlemeyi çok daha kolay hale getirir ( <xref:System.Windows.DependencyObject.SetValue%2A> her seferinde çağrı yapmaktan kaçınır ve bu çağrıyı sarmalayıcı içinde yalnızca bir kez yapabilir). Sarmalayıcı, özel bir bağımlılık özelliği kaydediyorsanız nasıl uygulanacaksa aynı şekilde uygulanır. Bağımlılık özelliği uygulama hakkında daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md) ve [bir bağımlılık özelliği Için sahip türü ekleme](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner ve Ekli Özellikler  
 Sahip sınıfı tarafından <xref:System.Windows.DependencyProperty.AddOwner%2A> iliştirilmiş bir özellik olarak tanımlanan bir bağımlılık özelliğini çağırabilirsiniz. Genellikle bunu yapmanın nedeni, önceden eklenmiş olan özelliği eklenmemiş bir bağımlılık özelliği olarak kullanıma sunmasıdır. Ardından, <xref:System.Windows.DependencyProperty.AddOwner%2A> dönüş değerini bağımlılık özelliği tanımlayıcısı olarak kullanılacak `public static readonly` bir alan olarak kullanıma sunar ve özelliğin üyeler tablosunda görünmesi ve eklenmemiş bir özelliği desteklemesi için uygun "sarmalayıcı" özelliklerini tanımlayacaksınız. sınıfınızın kullanımı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Çerçeve Özelliği Meta Verileri](framework-property-metadata.md)
