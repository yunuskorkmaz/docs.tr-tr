---
title: Bağımlılık Özelliği Meta Verisi
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 3d84510fce69e81929cbe9b6088e12aaf3409769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186361"
---
# <a name="dependency-property-metadata"></a>Bağımlılık Özelliği Meta Verisi
Özellik [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistemi, yansıma veya genel ortak dil çalışma süresi (CLR) özellikleri aracılığıyla bir özellik hakkında bildirilenlerin ötesine geçen bir meta veri raporlama sistemi içerir. Bağımlılık özelliği için meta veriler, bağımlılık özelliğini tanımlayan sınıf tarafından benzersiz olarak atanabilir, bağımlılık özelliği farklı bir sınıfa eklendiğinde değiştirilebilir ve özellikle tanımlayıcı taban sınıfından bağımlılık özelliği.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliklerini sınıflardaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] varolan bağımlılık özelliklerinin tüketici perspektifinden anladığınızı ve Bağımlılık Özellikleri Genel [Bakış'ı](dependency-properties-overview.md)okuduğunuzu varsayar. Bu konudaki örnekleri takip etmek için, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamaların nasıl yazAcağını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] da anlamalı ve bilmelidir.  
  
<a name="dp_metadata_contents"></a>
## <a name="how-dependency-property-metadata-is-used"></a>Bağımlılık Özelliği Meta verileri nasıl kullanılır?  
 Bağımlılık özelliği meta verileri, bağımlılık özelliğinin özelliklerini incelemek için sorgulanabilecek bir nesne olarak vardır. Bu meta verilere, belirli bir bağımlılık özelliğini işlerken özellik sistemi tarafından da sık sık erişilir. Bağımlılık özelliğinin meta veri nesnesi aşağıdaki türbilgileri içerebilir:  
  
- Bağımlılık özelliği için varsayılan değer, bağımlılık özelliği için yerel değer, stil, devralma vb. göre başka bir değer belirlenemezse. Bağımlılık özellikleri için değer atarken varsayılan değerlerin özellik sistemi tarafından kullanılan önceliğe nasıl katıldığına ilgili ayrıntılı bir tartışma için [bkz.](dependency-property-value-precedence.md)  
  
- Her sahibi-tür türü temelinde zorlama veya değişiklik bildirimi davranışlarını etkileyen geri arama uygulamalarına yapılan başvurular. Bu geri aramaların genellikle genel olmayan bir erişim düzeyiyle tanımlandığını unutmayın, bu nedenle başvurular izin verilen erişim kapsamınızda olmadığı sürece meta verilerden gerçek başvuruları almak genellikle mümkün değildir. Bağımlılık özelliği geri aramaları hakkında daha fazla bilgi için [bkz.](dependency-property-callbacks-and-validation.md)  
  
- Söz konusu bağımlılık özelliği WPF çerçeve düzeyinde bir özellik olarak kabul edilirse, meta veriler WPF çerçeve düzeyinde bağımlılık özelliği özellikleri içerebilir, bu da WPF çerçeve düzeyi düzeyi gibi hizmetler için bilgi ve durum durumu raporedebilir düzen motoru ve özellik devralma mantığı. Bağımlılık özelliği meta verilerinin bu yönü hakkında daha fazla bilgi için [Çerçeve Özelliği Meta verileri'ne](framework-property-metadata.md)bakın.  
  
<a name="APIs"></a>
## <a name="metadata-apis"></a>Meta veri API'leri  
 Özellik sistemi tarafından kullanılan meta veri bilgilerinin çoğunu <xref:System.Windows.PropertyMetadata> bildiren tür sınıftır. Bağımlılık özellikleri özellik sistemine kaydedildiğinde meta veri örnekleri isteğe bağlı olarak belirtilir ve kendilerini sahip olarak ekleyen veya temel sınıf bağımlılığından devraldıkları meta verileri geçersiz kılınan ek türler için yeniden belirtilebilir özellik tanımı. (Özellik kaydının meta verileri belirtmediği durumlarda, <xref:System.Windows.PropertyMetadata> o sınıf için varsayılan değerlerle varsayılan değerler oluşturulur.) Kayıtlı meta veriler, <xref:System.Windows.PropertyMetadata> bir <xref:System.Windows.DependencyObject> örneğin bağımlılık <xref:System.Windows.DependencyProperty.GetMetadata%2A> özelliğinden meta veri alan çeşitli aşırı yüklemeleri çağırdığınızda döndürülür.  
  
 Sınıf <xref:System.Windows.PropertyMetadata> daha sonra WPF çerçeve düzeyi sınıfları gibi mimari bölümler için daha özel meta veri sağlamak için türetilmiştir. <xref:System.Windows.UIPropertyMetadata>animasyon raporlaması <xref:System.Windows.FrameworkPropertyMetadata> ekler ve önceki bölümde belirtilen WPF çerçeve düzeyinde özellikleri sağlar. Bağımlılık özellikleri kaydedildiğinde, bu <xref:System.Windows.PropertyMetadata> türemiş sınıflara kaydedilebilir. Meta veriler incelendiğinde, daha <xref:System.Windows.PropertyMetadata> belirli özellikleri inceleyebilmeniz için taban türü türetilmiş sınıflara aktarılabilir.  
  
> [!NOTE]
> Belirtilebilen <xref:System.Windows.FrameworkPropertyMetadata> özellik özellikleri bazen bu belgede "bayraklar" olarak adlandırılır. Bağımlılık özelliği kayıtlarında veya meta veri geçersiz kılmalarında kullanılmak üzere yeni meta veri örnekleri oluşturduğunuzda, <xref:System.Windows.FrameworkPropertyMetadataOptions> bu değerleri bayrak yönünde numaralandırmayı kullanarak belirtir ve <xref:System.Windows.FrameworkPropertyMetadata> daha sonra numaralandırmanın büyük olasılıkla katlanılan değerlerini oluşturucuya sağlarsınız. Ancak, bir kez inşa edildikten <xref:System.Windows.FrameworkPropertyMetadata> sonra, bu seçenek özellikleri boolean özellikleri yerine yapı numaralandırma değeri bir dizi içinde maruz kalır. Boolean özellikleri, ilgilendiğiniz bilgileri almak için bayrak yönünde numaralandırma değerine maske uygulamanızı gerektirmek yerine her koşullu denetimi yapmanızı sağlar. Oluşturucu, kurucu imzanın uzunluğunu makul tutmak için koncatenated'i <xref:System.Windows.FrameworkPropertyMetadataOptions> kullanırken, gerçek oluşturulmuş meta veriler meta verileri sorgulamayı daha sezgisel hale getirmek için ayrık özellikleri ortaya çıkarır.  
  
<a name="override_or_subclass"></a>
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Meta verileri ne zaman geçersiz kılar, Ne Zaman Sınıf Türetmek  
 Özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistemi, bağımlılık özelliklerinin bazı özelliklerini tamamen yeniden uygulanmasına gerek kalmadan değiştirmek için yetenekler oluşturmuştur. Bu, bağımlılık özelliği için belirli bir türde var olan özellik meta verilerinin farklı bir örneğini oluşturarak gerçekleştirilir. Varolan bağımlılık özelliklerinin çoğunun sanal özellikler olmadığını, bu nedenle bunları yalnızca varolan üyenin gölgelemesi ile gerçekleştirilebilir.  
  
 Bir türüzerinde bir bağımlılık özelliği için etkinleştirmeye çalıştığınız senaryo varolan bağımlılık özelliklerinin özelliklerini değiştirerek gerçekleştirilemiyorsa, türetilmiş bir sınıf oluşturmak ve sonra özel bağımlılık özelliği ni bildirmek gerekebilir türemiş sınıfınızda. Özel bağımlılık [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği, API'ler tarafından tanımlanan bağımlılık özelliklerine aynı şekilde çalışır. Özel bağımlılık özellikleri hakkında daha fazla bilgi için [bkz.](custom-dependency-properties.md)  
  
 Geçersiz kılamayacağınız bir bağımlılık özelliğinin kayda değer özelliklerinden biri de değer türüdür. Gereksinim duyduğunuz yaklaşık davranışa sahip bir bağımlılık özelliği devralıyorsanız, ancak bunun için farklı bir türe ihtiyacınız varsa, özel bir bağımlılık özelliği uygulamanız ve belki de özellikleri tür dönüştürme veya diğer özel sınıfınızda uygulama. Ayrıca, varolan bir <xref:System.Windows.ValidateValueCallback>geri aramanın yerine geçemezsiniz, çünkü bu geri arama kayıt alanının kendisinde bulunur ve meta verileri içinde yoktur.  
  
<a name="scenarios"></a>
## <a name="scenarios-for-changing-existing-metadata"></a>Varolan Meta Verileri Değiştirme Senaryoları  
 Varolan bir bağımlılık özelliğinin meta verileriyle çalışıyorsanız, bağımlılık özelliği meta verilerini değiştirmek için sık karşılaşılan bir senaryo varsayılan değeri değiştirmektir. Özellik sistemi geri aramaları değiştirme veya ekleme daha gelişmiş bir senaryodur. Türetilmiş bir sınıfın uygulamanızın bağımlılık özellikleri arasında farklı ilişkileri varsa bunu yapmak isteyebilirsiniz. Hem kodu hem de bildirimsel kullanımı destekleyen bir programlama modeline sahip olmanın koşullarından biri, özelliklerin herhangi bir sırada ayarlanmasını sağlaması gerektiğidir. Bu nedenle, bağımlı özelliklerin bağlam olmadan tam zamanında ayarlanması gerekir ve bir oluşturucuda bulunabileceği gibi bir ayar sırası nın bilinmesine güvenemezsiniz. Özellik sisteminin bu yönü hakkında daha fazla bilgi için Bağımlılık [Özelliği Geri Aramaları ve Doğrulama](dependency-property-callbacks-and-validation.md)bölümüne bakın. Doğrulama geri aramalarının meta verilerin bir parçası olmadığını unutmayın; bağımlılık özelliği tanımlayıcısının bir parçasıdır. Bu nedenle, doğrulama geri aramaları meta verileri geçersiz kılınarak değiştirilemez.  
  
 Bazı durumlarda, varolan bağımlılık özelliklerindeki WPF çerçeve düzeyinde özellik meta veri seçeneklerini de değiştirmek isteyebilirsiniz. Bu seçenekler, WPF çerçeve düzeyi özellikleri hakkında bilinen belirli koşullu durumları düzen sistemi gibi diğer WPF çerçeve düzeyindeki işlemlere iletir.  Seçenekleri ayarlama genellikle yalnızca yeni bir bağımlılık özelliği kaydederken yapılır, ancak WPF çerçeve düzeyindeözellik meta verilerini bir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> <xref:System.Windows.DependencyProperty.AddOwner%2A> veya çağrının parçası olarak değiştirmek de mümkündür. Kullanılacak belirli değerler ve daha fazla bilgi için [Çerçeve Özelliği Meta verilerine](framework-property-metadata.md)bakın. Bu seçeneklerin yeni kaydedilmiş bir bağımlılık özelliği için nasıl ayarlanması gerektiğiyle ilgili daha fazla bilgi için [bkz.](custom-dependency-properties.md)  
  
<a name="dp_override_metadata"></a>
### <a name="overriding-metadata"></a>Meta verileri geçersiz kılma  
 Meta verileri geçersiz kılmanın amacı, öncelikle türünüzde var olduğu gibi bağımlılık özelliğine uygulanan çeşitli meta veri türetilmiş davranışları değiştirme fırsatına sahip olmaktır. Bunun nedenleri [Metadata](#dp_metadata_contents) bölümünde daha ayrıntılı olarak açıklanmıştır. Bazı kod örneklerini içeren daha fazla bilgi [için, Bağımlılık Özelliği için Meta Verilerini Geçersiz Kılma bölümüne](how-to-override-metadata-for-a-dependency-property.md)bakın.  
  
 Özellik meta verileri, kayıt çağrısı sırasında bir bağımlılık<xref:System.Windows.DependencyProperty.Register%2A>özelliği için sağlanabilir ( ). Ancak, çoğu durumda, bu bağımlılık özelliği devraldığında sınıfınız için türe özgü meta verileri sağlamak isteyebilirsiniz. Yöntemi arayarak <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> bunu yapabilirsiniz.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'lerden bir örnek <xref:System.Windows.FrameworkElement> olarak, sınıf bağımlılık özelliğini <xref:System.Windows.UIElement.Focusable%2A> ilk kaydeden türüdür. Ancak <xref:System.Windows.Controls.Control> sınıf, bağımlılık özelliğinin kendi ilk varsayılan değerini sağlaması için meta `false` `true`verileri geçersiz kılar, bu <xref:System.Windows.UIElement.Focusable%2A> değeri "' den " olarak değiştirir ve özgün uygulamayı yeniden kullanır.  
  
 Meta verileri geçersiz kaldığınızda, farklı meta veri özellikleri birleştirilir veya değiştirilir.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>birleştirilir. Yeni <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>bir , bu geri arama meta verilerde depolanır eklerseniz. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, değeri <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> meta verilerde belirtilen en yakın atadan bir başvuru olarak yükseltilir.  
  
- Gerçek özellik sistemi <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> davranışı, hiyerarşideki tüm meta veri sahiplerinin uygulamalarının korunması ve bir tabloya eklenmesidir ve özellik sistemi tarafından yürütme sırası en çok türetilen sınıfın geri aramaları önce çağrılır.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>değiştirilir. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.DefaultValue%2A> belirtmezseniz, değeri <xref:System.Windows.PropertyMetadata.DefaultValue%2A> meta verilerde onu belirten en yakın atadan gelir.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>uygulamaları değiştirilir. Yeni <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>bir , bu geri arama meta verilerde depolanır eklerseniz. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> belirtmezseniz, değeri <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> meta verilerde belirtilen en yakın atadan bir başvuru olarak yükseltilir.  
  
- Özellik sistemi davranışı, yalnızca <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hemen meta verilerde çağrılan olmasıdır. Hiyerarşideki diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamalara yapılan atıflar korunur.  
  
 Bu davranış, türetilmiş meta veri sınıfları tarafından <xref:System.Windows.PropertyMetadata.Merge%2A>uygulanır ve geçersiz kılınabilir.  
  
#### <a name="overriding-attached-property-metadata"></a>Eklenmiş Özellik Meta verilerini geçersiz kılma  
 In, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekli özellikleri bağımlılık özellikleri olarak uygulanır. Bu, tek tek sınıfların geçersiz kıldığı özellik meta verilerine de sahip oldukları anlamına gelir. Ekli bir özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için kapsam belirleme hususlar genellikle herhangi <xref:System.Windows.DependencyObject> bir bağlı özelliği onlara ayarlanmış olabilir. Bu nedenle, türemiş herhangi bir <xref:System.Windows.DependencyObject> sınıf, sınıfın bir örneğinde ayarlanabileceğinden, ekli herhangi bir özellik için meta verileri geçersiz kılabilir. Varsayılan değerleri, geri aramaları veya WPF çerçeve düzeyinde karakteristik raporlama özelliklerini geçersiz kılabilir. Ekli özellik sınıfınızın bir örneğinde ayarlanmışsa, bunlar özellik meta veri özelliklerini geçersiz kılar. Örneğin, geçersiz kılma değerinizin sınıfınörneklerinde ekli özelliğin değeri olarak bildirilmiş olması gibi varsayılan değeri geçersiz kılabilirsiniz.  
  
> [!NOTE]
> Özellik <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> ekli özellikler için ilgili değildir.  
  
<a name="dp_add_owner"></a>
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Varolan Bağımlılık Özelliğinin Sahibi Olarak Sınıf Ekleme  
 Bir sınıf, <xref:System.Windows.DependencyProperty.AddOwner%2A> yöntemi kullanarak, daha önce kaydedilmiş bir bağımlılık özelliğinin sahibi olarak kendisini ekleyebilir. Bu, sınıfın özgün olarak farklı bir tür için kaydedilmiş bir bağımlılık özelliğini kullanmasını sağlar. Ekleme sınıfı genellikle, bağımlılık özelliğini ilk olarak sahip olarak kaydeden türün türetilmiş bir sınıfı değildir. Bu, özgün sahip sınıfı ve eklenen sınıf aynı gerçek sınıf hiyerarşisinde olmadan sınıfınızın ve türetilmiş sınıflarınızın bir bağımlılık özelliği uygulamasını "devralmasına" olanak tanır. Buna ek olarak, ekleme sınıfı (ve tüm türetilmiş sınıflar da) daha sonra özgün bağımlılık özelliği için türe özgü meta verileri sağlayabilir.  
  
 Yanı sıra mülkiyet sistemi yardımcı yöntemleri ile sahibi olarak kendini ekleyerek, ekleme sınıf bağımlılık özelliği] hem kod ve biçimlendirme maruz kalma ile mülkiyet sisteminde tam bir katılımcı yapmak için kendisi üzerinde ek kamu üyeleri beyan etmelidir . Varolan bir bağımlılık özelliği ekleyen bir sınıf, bu bağımlılık özelliği için nesne modelini yeni bir özel bağımlılık özelliği tanımlayan bir sınıfla aynı sorumluluklara sahiptir. Bu tür ilk üye bir bağımlılık özelliği tanımlayıcı alanıdır. Bu alan, `public static readonly` <xref:System.Windows.DependencyProperty.AddOwner%2A> çağrının <xref:System.Windows.DependencyProperty>geri dönüş değerine atanan bir tür alanı olmalıdır. Tanımlamak için ikinci üye ortak dil çalışma zamanı (CLR) "sarmalayıcı" özelliğidir. Sarmalayıcı, bağımlılık özelliğinizi kodda manipüle etmeyi çok daha kullanışlı <xref:System.Windows.DependencyObject.SetValue%2A> hale getirir (her seferinde arama yapmaktan kaçınırsınız ve bu aramayı sarıcının kendisinde yalnızca bir kez yapabilirsiniz). Sarıcı, özel bir bağımlılık özelliği ni kaydediyorsanız nasıl uygulanacağı yla aynı şekilde uygulanır. Bağımlılık özelliği uygulama hakkında daha fazla bilgi için Bkz. [Özel Bağımlılık Özellikleri](custom-dependency-properties.md) ve Bağımlılık Özelliği için Sahip Türü [Ekle.](how-to-add-an-owner-type-for-a-dependency-property.md)  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner ve Ekli Özellikler  
 Sahibi sınıf <xref:System.Windows.DependencyProperty.AddOwner%2A> tarafından ekli bir özellik olarak tanımlanan bir bağımlılık özelliği için arayabilirsiniz. Genellikle bunu yapmanın nedeni, daha önce bağlı olmayan bir bağımlılık özelliği olarak bağlı olmayan özelliği ortaya çıkarmaktır. Daha <xref:System.Windows.DependencyProperty.AddOwner%2A> sonra, geri dönüş `public static readonly` değerini bağımlılık özelliği tanımlayıcısı olarak kullanılmak üzere bir alan olarak ortaya çıkarır ve özelliğin üyeler tablosunda görünmesi ve sınıfınızdaki eklenmemiş bir özellik kullanımını desteklemesi için uygun "sarmalayıcı" özelliklerini tanımlarsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Çerçeve Özelliği Meta Verileri](framework-property-metadata.md)
