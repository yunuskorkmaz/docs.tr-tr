---
title: WPF için XAML ve Özel Sınıflar
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: acf3ba12a9a7e6ba9a8e378892098f5f265a23d9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461806"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF için XAML ve Özel Sınıflar
XAML içinde uygulandığı şekilde [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] çerçevelerini destekleyen özel bir sınıf veya yapı, tüm tanımlama yeteneği [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] dil ve ardından erişim kullanarak XAML biçimlendirmesi. Bir karışımını kullanabilirsiniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-tanımlanan türleri ve aynı biçimlendirme dosyasında özel türlerinizi genellikle XAML ad alanı öneki özel türleri eşleyerek. Bu konuda, özel bir sınıf bir XAML öğesi olarak kullanılabilir olması için karşılaması gereken gereksinimleri anlatılmaktadır.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Uygulamaların veya derlemelerin özel sınıflar  
 XAML içinde kullanılan özel sınıflar, iki farklı şekilde tanımlanabilir: arka plan kod veya birincil üreten diğer kod içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulaması veya farklı bir sınıfta bir yürütülebilir dosya gibi ayrı bir derleme veya bir sınıf kitaplığı kullanılan DLL. Bu yaklaşımların her birinin belirli avantajları ve dezavantajları vardır.  
  
-   Bir sınıf kitaplığı oluşturma gibi özel sınıflar birçok farklı olası uygulamalar arasında paylaşılabilir avantajlarındandır. Ayrı bir kitaplık ayrıca uygulamalar gibi sürüm oluşturma sorunları denetimi kolaylaştırır ve burada bir kök öğe üzerinde bir XAML sayfası olarak hedeflenen sınıf kullanım, bir sınıf oluşturma basitleştirir.  
  
-   Özel sınıflar uygulamasında tanımlama avantajı, bu tekniği görece basit ve dağıtım ve ayrı derlemeler ana uygulamanın yürütülebilir ötesinde aldığımızda karşılaştığı sınama sorunlarını en aza indirir olmasıdır.  
  
-   Aynı veya farklı bir derlemede tanımlanan olsun, özel sınıflar XML ad alanı ve CLR ad uzayı arasında XAML içinde öğeleri olarak kullanılabilmesi için eşlenmesi gerekir. Bkz: [XAML ad alanları ve WPF XAML için Namespace eşlemesi](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML öğesi olarak özel bir sınıf için gereksinimleri  
 Bir nesne öğesi olarak oluşturulacak oluşturabilmek adına sınıfınıza aşağıdaki gereksinimleri karşılaması gerekir:  
  
-   Özel sınıfınıza genel olmalıdır ve bir varsayılan (parametresiz) ortak oluşturucu destekler. (Aşağıdaki bölümde yapıları ile ilgili notlar için bkz.)  
  
-   Özel sınıfınıza iç içe geçmiş bir sınıf olmalıdır. İç içe geçmiş sınıflar ve onların genel CLR kullanım söz dizimine "dot" uğratabilecek diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve/veya iliştirilmiş özellikler gibi XAML özellikleri.  
  
 Nesne öğesi sözdizimi etkinleştirmeye ek olarak, nesne tanımınızı ayrıca söz konusu nesne değer türü olarak ele herhangi bir genel özellikler için özellik öğesi sözdizimini sağlar. Nesne artık bir nesne öğesi olarak oluşturulabilir ve böyle bir özellik özellik öğe değerini doldurabilir olmasıdır.  
  
### <a name="structures"></a>Yapılar  
 Özel türler her zaman XAML içinde oluşturulmuş mümkün olduğu gibi tanımladığınız yapıları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Bunun nedeni, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] derleyiciler varsayılanlarına tüm özellik değerlerini başlatan bir yapı için bir varsayılan oluşturucu örtük olarak oluşturun. Bazı durumlarda, varsayılan yapı davranışı ve/veya nesne öğesi kullanımı bir yapı için uygun değil. Bu yapı dolgu değerleri ve işlev için kavramsal olarak burada yer alan değerleri dışlayan yorumlaması olabilir ve bu nedenle özelliklerini hiçbiri ayarlanabilir birleşim olarak tasarlandığından olabilir. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] böyle bir yapı örneğidir <xref:System.Windows.GridLength>. Genellikle, farklı ınterpretations ya da yapının değerlerinin modları oluşturma dize kurallarını kullanarak öznitelik formunda değerleri belirtilebilir, bu tür yapıları bir tür dönüştürücüsü uygulamalıdır. Yapısı, varsayılan olmayan bir oluşturucu aracılığıyla kod oluşturma için benzer bir davranış da sunmalıdır.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>XAML öznitelik olarak özel bir sınıf özelliklerini gereksinimleri  
 Özellikleri bir değere göre türlerinin (örneğin, basit bir tür) başvuru veya bir sınıf için varsayılan bir oluşturucu veya XAML işlemci erişebilen bir adanmış bir tür dönüştürücüsü sahip türü kullanın. CLR XAML uygulamasında, XAML işlemci ya da dil temelleri için yerleşik destek veya uygulama bu tür dönüştürücüleri Bul <xref:System.ComponentModel.TypeConverterAttribute> sağlayan bir tür veya üye, tür tanımlarını yedekleme  
  
 Alternatif olarak, özellik, bir soyut sınıfı türü veya arabirim başvuruda bulunabilir. Soyut sınıflar veya arabirimler için XAML ayrıştırma için özellik değeri arabirimini uygulaması pratik sınıf örneklerinin veya soyut sınıftan türetilen türler örnekleri ile doldurulmalıdır beklenir.  
  
 Özellikler, bir soyut sınıfta bildirilen, ancak yalnızca soyut sınıftan türeyen pratik sınıflarda ayarlanabilir. Object öğesi sınıfı için hiç oluşturma sınıfı hakkında genel bir varsayılan oluşturucu gerektirdiğinden budur.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Öznitelik sözdizimi TypeConverter etkin  
 Sınıf düzeyinde ayrılmış, öznitelik atanmış bir tür dönüştürücüsü sağlarsanız, bu tür örneği için gereken herhangi bir özelliği için öznitelik sözdizimi uygulanan tür dönüştürme sağlar. Bir tür dönüştürücüsü türündeki nesne öğesi kullanımı etkinleştirmez; yalnızca bu tür için varsayılan bir oluşturucu varlığını nesne öğesi kullanımı sağlar. Türü nesne öğesi sözdizimi desteklemedikçe bu nedenle, tür dönüştürücüsü etkin olan özellikleri genel olarak bakıldığında özellik sözdiziminde kullanılabilir değildir. Bu özellik öğesi sözdizimini belirtebilirsiniz ancak bir dize içermesi özellik öğesi olması istisnadır. Bu kullanım için bir öznitelik sözdizimi kullanımı gerçekten temelde eşdeğerdir ve böyle bir kullanımı olmadığı sürece bir öznitelik değeri daha sağlam boşluk işleme gereksinimini yaygın değildir. Örneğin, bir dize alır bir özellik öğesi kullanımı ve eşdeğer öznitelik kullanımı verilmiştir:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Örnekler nerede öznitelik sözdizimi izin verilir, ancak XAML bir nesne öğesi içeren bir özellik öğesi sözdizimine izin verilmeyen özellikleri ele çeşitli özelliklerini <xref:System.Windows.Input.Cursor> türü. <xref:System.Windows.Input.Cursor> Sınıfında özel bir tür dönüştürücüsü <xref:System.Windows.Input.CursorConverter>, varsayılan bir oluşturucu oluşturmaz, ancak bu nedenle <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği yalnızca ayarlanabilir öznitelik söz dizimi aracılığıyla rağmen gerçek <xref:System.Windows.Input.Cursor> türü olan bir başvuru türü.  
  
### <a name="per-property-type-converters"></a>Özellik başına tür dönüştürücüleri  
 Alternatif olarak, özellik, bir tür dönüştürücüsü özellik düzeyinde bildirebilir. Bu "özelliği satır içi türündeki nesneler için girdi olarak gelen dize değerleri özniteliğinin işleyerek örnekleyen bir mini dil" sağlayan bir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> işlemi uygun türüne göre. Bu kolaylık erişimci sağlamak için genellikle gerçekleştirilir ve tek bir özelliği ayarlamak XAML etkinleştirmek anlamına gelir değil. Ancak, ayrıca, varolan kullanmak istediğiniz öznitelikler için tür dönüştürücüleri kullanılacak mümkündür [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] varsayılan bir oluşturucu ya da bir öznitelik türü dönüştürücü vermezsiniz türleri. Örneklerden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API alan belirli özellikleri olan <xref:System.Globalization.CultureInfo> türü. Bu durumda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] var olan Microsoft .NET Framework kullanılan <xref:System.Globalization.CultureInfo> çerçeveleri, önceki sürümlerinde kullanılan uyumluluğu ve geçiş senaryoları için daha iyi tür ancak <xref:System.Globalization.CultureInfo> türü gerekli desteği oluşturucuları veya doğrudan bir XAML özellik değeri kullanılabilmesi için tür düzeyi tür dönüştürme.  
  
 XAML kullanım olan bir özelliği kullanıma sunun, her özellikle denetim yazarı, varsa, kesin bir bağımlılık özelliği ile bu özelliği yedekleyen düşünmelisiniz. Bu varolan kullanıyorsanız özellikle geçerlidir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] XAML işlemci uygulamasında kullanarak performansı artırmak için <xref:System.Windows.DependencyProperty> yedekleme. Bağımlılık özelliği, kullanıcıların bir XAML erişilebilir özelliği için beklenen gelir, bir özellik için özellik sistemi özellikleri açığa çıkarır. Bu, animasyon, veri bağlama ve stil desteği gibi özellikler içerir. Daha fazla bilgi için [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [XAML yükleme ve bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Yazma ve bir tür dönüştürücüsü öznitelik atanıyor  
 Özel bir yazmak zaman zaman gerekir <xref:System.ComponentModel.TypeConverter> türetilmiş sınıf, özellik türü için tür dönüştürme sağlamak için. Öğesinden türetilen ve XAML kullanımları destekleyen bir tür dönüştürücüsü oluşturmayı ve nasıl uygulanacağı hakkında yönergeler için <xref:System.ComponentModel.TypeConverterAttribute>, bkz: [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>XAML olay işleyicisi öznitelik sözdizimi olaylara özel bir sınıf için gereksinimleri  
 Olarak kullanılabilir bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay, olay varsayılan bir oluşturucu destekleyen bir sınıfta ortak bir olay olarak sunulmalıdır veya üzerinde bir soyut sınıfı türetilen sınıflarda olay burada erişilebilir. Gönderilmiş bir olay olarak kolayca kullanılabilmesi için [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay açık uygulamak `add` ve `remove` eklemek ve kaldırmak için işleyiciler yöntemleri [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay imzası ve bu işleyicileri iletme<xref:System.Windows.UIElement.AddHandler%2A>ve <xref:System.Windows.UIElement.RemoveHandler%2A> yöntemleri. Bu yöntemler, ekleyin veya olay bağlı örneğinde yönlendirilmiş olay işleyici deposuna işleyicileri kaldırın.  
  
> [!NOTE]
>  Kullanarak doğrudan yönlendirilmiş olayları için işleyiciler kaydetmek mümkündür <xref:System.Windows.UIElement.AddHandler%2A>ve kasıtlı değildir tanımlamak için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] yönlendirilmiş olayı ortaya koyan olay. Bu genellikle olay işleyicileri ekleme için XAML söz dizimi özniteliği izin vermez ve sonuçta elde edilen sınıfınıza bu türün özelliklerini daha az saydam bir XAML görünümünü sunacaktır önerilmez.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Koleksiyon Özellikleri yazma  
 Bir koleksiyon türü alan özellikleri koleksiyona eklenen nesneler belirtmenize olanak tanıyan bir XAML söz dizimi var. Bu söz dizimi iki önemli özelliklere sahiptir.  
  
-   Koleksiyon nesnesi nesnesini nesne öğesi sözdiziminde belirtilmesi gerekmez. Bu koleksiyon türünün varolup olmadığını örtük olarak, her bir koleksiyon türü alan XAML içinde bir özellik belirtin.  
  
-   Koleksiyon özelliği biçimlendirme içinde alt öğeleri koleksiyon üyelerinin olacak işlenir. Normalde, bir koleksiyonun üyelerini kod erişimi listesi/sözlük yöntemleri gibi gerçekleştirilir `Add`, veya bir dizin oluşturucu. Ancak XAML söz dizimi, yöntemler veya dizin oluşturucular desteklemez (özel durum: XAML 2009 desteklediği yöntemler, ancak XAML 2009 kullanarak olası WPF kullanımları kısıtlar; bkz [XAML 2009 dil özellikleri](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). Koleksiyonlar açıkça öğe ağacındaki oluşturmaya yönelik yaygın bir gereksinim olan ve bu bildirim temelli XAML koleksiyonlarında doldurmak için bir yönteme gerekir. Bu nedenle, bir koleksiyon özelliği alt öğelerinin koleksiyonunu özellik türü değeri koleksiyona ekleyerek işlenir.  
  
 .NET Framework XAML hizmetlerinde uygulama ve bu nedenle WPF XAML işlemcisi bir koleksiyon özelliği nelerden için aşağıdaki tanımını kullanır. Özelliğin özellik türü, aşağıdakilerden birini uygulamalıdır:  
  
-   Implements <xref:System.Collections.IList>.  
  
-   Implements <xref:System.Collections.IDictionary> veya genel eş değeri (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Öğesinden türetilen <xref:System.Array> (XAML içindeki diziler hakkında daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implements <xref:System.Windows.Markup.IAddChild> (bir arabirim tarafından tanımlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Her CLR içinde bu tür bir `Add` Nesne grafiğini oluştururken, temel toplulukta öğeleri eklemek XAML işlemcisi tarafından kullanılan yöntem.  
  
> [!NOTE]
>  Genel `List` ve `Dictionary` arabirimleri (<xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602>) koleksiyonu algılama tarafından desteklenmeyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci. Ancak, kullanabileceğiniz <xref:System.Collections.Generic.List%601> uyguladığından, sınıf bir temel sınıf <xref:System.Collections.IList> doğrudan veya <xref:System.Collections.Generic.Dictionary%602> bir temel sınıf olarak uyguladığından, <xref:System.Collections.IDictionary> doğrudan.  
  
 Bir koleksiyon alır bir özellik bildirdiğinizde, bu özellik değeri türü yeni örneklerini nasıl başlatılır hakkında dikkatli olun. Özelliği bir bağımlılık özelliği olarak uyguluyorsanız değil, ardından koleksiyon türü oluşturucusunu çağırır destek alanı kullanma özelliği olması yeterlidir. Bağımlılık özelliği özelliğinizi ise koleksiyon özelliği varsayılan tür Oluşturucu bir parçası olarak başlatmak gerekebilir. Bu bağımlılık özelliği meta verilerden varsayılan değerini alır ve statik ve paylaşılan bir koleksiyon için bir koleksiyon özelliği ilk değerini genellikle istemediğiniz olmasıdır. Bir koleksiyon örnek içeren her türü örneği başına olması gerekir. Daha fazla bilgi için [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Özel koleksiyon türü, koleksiyon özelliği için uygulayabilirsiniz. Örtülü koleksiyon özelliği kullanımı nedeniyle, özel koleksiyon türü XAML içinde örtük olarak kullanılabilmesi için bir varsayılan oluşturucu sağlayın gerekmez. Ancak toplama türü için varsayılan bir oluşturucu isteğe bağlı olarak sağlayabilirsiniz. Bu faydalı bir uygulama olabilir. Varsayılan bir oluşturucu sağlamazsanız, bir nesne öğesi olarak açıkça bildiremezsiniz. Bazı biçimlendirme yazarları açık koleksiyonu işaretleme stili birkaç görmek tercih edebilirsiniz. Ayrıca, özellik değeri olarak koleksiyon türüne kullanan yeni nesneler oluşturduğunuzda, varsayılan bir oluşturucu başlatma gereksinimlerini basitleştirir.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>XAML İçerik özellikleri bildirme  
 XAML dil kavramını tanımlar bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik özelliği. Nesne sözdizimi içinde kullanılabilir olan her sınıf, tam olarak bir XAML İçerik özelliğine sahip olabilir. Sınıfınız için XAML içerik özelliği bir özelliği bildirme uygulamak <xref:System.Windows.Markup.ContentPropertyAttribute> sınıf tanımının bir parçası olarak. Hedeflenen XAML içerik özelliği adını <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> öznitelik. Özellik bir dize olarak ada göre değil bir yansıma yapısı gibi belirtilir <xref:System.Reflection.PropertyInfo>.  
  
 XAML içerik özelliği bir koleksiyon özelliğini belirtebilirsiniz. Object öğesi bir veya daha fazla alt öğeleri, herhangi bir müdahalede bulunan koleksiyon nesne öğeleri veya özellik öğesi etiketleri olmadan yapabildiği olabilir, bu özellik için bir kullanım sonuçlanır. Bu öğelerden sonra XAML İçerik özelliğinin değeri olarak kabul edilir ve yedekleme koleksiyon örneğine eklenen.  
  
 Özellik türü var olan bazı XAML İçerik özellikleri kullanmak `Object`. Bu basit sürebilir özellik değerlerinin gibi içerik bir XAML sağlar bir <xref:System.String> yanı sıra tek başvurusu nesne değeri. Bu model izlerseniz, işleme olası türlerinin yanı sıra tür belirleme türünüz sorumludur. Sık karşılaşılan nedeni bir <xref:System.Object> türüdür (Bu varsayılan sunu işleme alır) bir dize olarak nesne içeriğini ekleme her iki basit bir araç desteklemek için veya ekleme Gelişmiş bir yol nesnesi belirten bir varsayılan olmayan sunu içeriği içerik veya ek veriler.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>XAML seri hale getirme  
 IF gibi belirli senaryolarda, bir denetim yazarı, XAML içinde oluşturulabilir herhangi bir nesne temsili de geri denk XAML biçimlendirmesi serileştirilecek sağlamak isteyebilirsiniz. Serileştirme gereksinimleri, bu konuda açıklanan değil. Bkz: [denetim yazmaya genel bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md) ve [öğe ağacı ve Serileştirme](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [XAML Yükleme ve Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
