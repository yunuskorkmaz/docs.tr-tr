---
title: WPF için XAML ve Özel Sınıflar
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 35c4e23298a8af9fdba92b7e4b6231c08861cc72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549324"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF için XAML ve Özel Sınıflar
Uygulanan gibi XAML [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] çerçeveleri destekleyen özel sınıf veya yapı birinde tanımlama yeteneği [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] dil ve ardından erişim XAML biçimlendirme kullanarak sınıfı. Bir karışımını kullanabilirsiniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-tanımlı türleri ve özel türlerinizi aynı biçimlendirme dosyası içinde genellikle XAML ad alanı öneki özel türler eşleyerek. Bu konuda bir XAML öğesi olarak kullanılabilmesi için özel bir sınıf getirmelidir gereksinimleri açıklanmaktadır.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Uygulamalar veya derlemeler özel sınıflar  
 XAML'de kullanılan özel sınıflar iki farklı şekilde tanımlanabilir: arka plan kodu veya birincil üreten başka bir kod içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulaması veya bir yürütülebilir dosya gibi ayrı bir derleme sınıfında ya da bir sınıf kitaplığı kullanılan DLL olarak. Bu yaklaşımların her birinin belirli avantajları ve dezavantajları vardır.  
  
-   Bir sınıf kitaplığı oluşturmak avantajı, bu tür özel sınıflar birçok farklı olası uygulamalar arasında paylaşılabilir olmasıdır. Ayrı bir kitaplık ayrıca denetlemek için sürüm sorunları uygulamaların kolaylaştırır ve hedeflenen sınıf kullanım XAML sayfası üzerinde bir kök öğe olarak olduğu bir sınıf oluşturma basitleştirir.  
  
-   Uygulama özel sınıfları tanımlama avantajı, bu teknik görece basit ve dağıtım ve yürütülebilir ana uygulamanın ötesinde ayrı derlemeler aldığımızda test sorunları en aza indirir olmasıdır.  
  
-   Aynı veya farklı bir derlemede tanımlanan olup olmadığını özel sınıflar XAML'de öğeleri olarak kullanılması için XML ad alanı ve CLR ad arasında eşlenmesi gerekir. Bkz: [XAML ad uzayları ve WPF XAML için Namespace eşleme](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML öğesi olarak özel bir sınıf için gereksinimleri  
 Bir nesne öğesi olarak oluşturulmasını oluşturabilmek, sınıfınıza aşağıdaki gereksinimleri karşılaması gerekir:  
  
-   Özel bir sınıf, ortak ve varsayılan (parametresiz) ortak oluşturucu destekler. (Bölüm yapıları ilgili notları aşağıdaki bakın.)  
  
-   İç içe geçmiş sınıf, özel bir sınıf olmalıdır. İç içe geçmiş sınıflar ve onların genel CLR kullanım sözdizimi "nokta" müdahale diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve/veya ekli özellikler gibi XAML özellikleri.  
  
 Nesne tanımı nesne öğesi sözdizimi etkinleştirmeye ek olarak, bu nesne değeri türü olarak ele herhangi bir ortak özellikler için özellik öğesi sözdizimini de sağlar. Nesne bir nesne öğesi olarak şimdi oluşturulabilir ve böyle bir özellik özellik öğesi değerini doldurabilir olmasıdır.  
  
### <a name="structures"></a>Yapılar  
 Özel türler her zaman XAML'de oluşturulması mümkün olduğu gibi tanımladığınız yapıları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Bunun nedeni, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] derleyicileri varsayılanlarına tüm özellik değerlerini başlatır yapısı için varsayılan bir oluşturucu örtük olarak oluşturun. Bazı durumlarda, varsayılan yapım davranışı ve/veya nesne öğesi için kullanım bir yapı arzu değil. Bu yapı dolgu değerleri ve işlevi kavramsal olarak burada yer alan değerler birbirini dışlayan yorumlar olabilir ve bu nedenle özelliklerini hiçbiri ayarlanabilir UNION tasarlandığından olabilir. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] böyle bir yapı örneği <xref:System.Windows.GridLength>. Genellikle, farklı yorumlar veya modları yapısı değerlerin oluşturma dize kurallarını kullanarak özniteliği formda değerleri belirtilebilir, böyle yapıları tür dönüştürücüsünü uygulamanız gerekir. Yapı Ayrıca varsayılan olmayan bir oluşturucu aracılığıyla kod oluşturma için benzer davranış maruz bırakmamalısınız.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Özel bir sınıf özelliklerini XAML nitelikleri gereksinimleri  
 Özellikler bir değer tarafından türü (örneğin, bir temel eleman) başvuru veya varsayılan bir oluşturucu veya XAML işlemci erişmek için bir özel tür dönüştürücüsünü sahip türü için bir sınıf kullanma. CLR XAML uygulamasında XAML işlemcileri ya da bu tür dönüştürücüleri dil temelleri için yerleşik destek veya uygulama bulmak <xref:System.ComponentModel.TypeConverterAttribute> bir türe veya tür tanımları yedekleme içinde üyesi  
  
 Alternatif olarak, özellik, bir Özet sınıf türü ya da bir arabirim başvuruda bulunabilir. Soyut sınıflar veya arabirimler için XAML ayrıştırma için özellik değeri arabirimini uygulayan pratik sınıf örneklerini veya soyut sınıftan türetilen türler örnekleri ile doldurulması gerekir beklenir.  
  
 Özellikler bir Özet sınıf üzerinde bildirilen, ancak yalnızca soyut sınıftan türeyen pratik sınıfları ayarlanabilir. Object öğesi sınıfı için hiç oluşturma sınıfı üzerinde ortak varsayılan bir oluşturucu gerektirdiğinden budur.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Öznitelik sözdizimi Typeconverter'a etkin  
 Sınıf düzeyinde ayrılmış, öznitelikli tür dönüştürücüsünü sağlarsanız, uygulanan tür dönüştürme türü örneği oluşturmak için gereken herhangi bir özelliği için öznitelik sözdizimi sağlar. Tür dönüştürücü nesne öğesi kullanımı türü etkinleştirmez; yalnızca bu tür için varsayılan bir oluşturucu varlığını nesne öğesi kullanımı sağlar. Türü ayrıca nesne öğesi sözdizimi desteklemedikçe bu nedenle, tür dönüştürücüsünü etkin özellikleri genel olarak bakıldığında özellik sözdiziminde kullanılabilir değildir. Bu özellik öğe sözdizimini belirtmek ancak bir dize içermesi özellik öğesi olması istisnadır. Bu kullanım için bir öznitelik sözdizimi kullanımı gerçekten temelde eşdeğerdir ve öznitelik değeri daha sağlam boşluk işleme gereksinimini değilse bu tür bir kullanım ortak değil. Örneğin, bir dize alır bir özellik öğesi kullanımı ve eşdeğer öznitelik kullanımı verilmiştir:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Burada öznitelik sözdizimi izin verilir ancak XAML object öğesini içeren özellik öğesi sözdizimini izin verilmeyen özellikleri örnekler ele çeşitli özellikleri <xref:System.Windows.Input.Cursor> türü. <xref:System.Windows.Input.Cursor> Sınıfına sahip bir özel tür dönüştürücüsünü <xref:System.Windows.Input.CursorConverter>, varsayılan bir oluşturucu oluşturmaz, ancak bu nedenle <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği yalnızca ayarlanabilir öznitelik sözdizimi rağmen gerçek <xref:System.Windows.Input.Cursor> türü olan bir başvuru türü.  
  
### <a name="per-property-type-converters"></a>Özellik başına tür dönüştürücüleri  
 Alternatif olarak, özellik türü dönüştürücü özelliği düzeyinde bildirebilir. Bu "özelliği satır içi tür nesneleri için giriş olarak özniteliğinin gelen dize değerlerini işleyerek örneklendirir mini bir dil" sağlayan bir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> işlemi uygun türüne bağlı. Bu bir kolaylık erişimcisi sağlamak için genellikle yapılır ve tek bir özellik XAML'de ayarlama etkinleştirmek anlamına gelir değil. Ancak, aynı zamanda varolan kullanmak istediğiniz öznitelikler için tür dönüştürücüleri kullanmak mümkündür [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] varsayılan bir oluşturucu veya öznitelikli tür dönüştürücüsünü sağlamazsanız türleri. Örneklerinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API ele belirli özellikleri olan <xref:System.Globalization.CultureInfo> türü. Bu durumda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] var olan Microsoft .NET Framework kullanılan <xref:System.Globalization.CultureInfo> daha iyi çerçeveleri, önceki sürümlerinde kullanılan uyumluluğu ve geçiş senaryosu için türü ancak <xref:System.Globalization.CultureInfo> türü desteklemediği gerekli Oluşturucular veya türü düzeyi tür dönüşümü doğrudan XAML özellik değeri olarak kullanılabilir.  
  
 XAML kullanımına sahip bir özellik kullanıma olduğunda, özellikle bir denetim yazarı varsa, kesinlikle bu özellik bir bağımlılık özelliği ile yedekleme düşünmelisiniz. Bu varolan kullanırsanız, özellikle geçerlidir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] XAML işlemci uygulaması kullanarak performansı artırabilir çünkü <xref:System.Windows.DependencyProperty> yedekleme. Bağımlılık özelliği kullanıcılar XAML erişilebilir özelliği için beklenen gelir, bir özellik için özellik sistemi özellikleri açığa çıkarır. Animasyon, veri bağlama ve stil desteği gibi özellikler içerir. Daha fazla bilgi için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [XAML yükleme ve bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Yazma ve tür dönüştürücüsünü öznitelik atanıyor  
 Bazen özel bir yazma gerekir <xref:System.ComponentModel.TypeConverter> türetilmiş sınıf özelliği türünüz için tür dönüştürme sağlayın. Öğesinden türetilen ve XAML kullanımları destekleyebilen bir türü dönüştürücü oluşturmanız ve nasıl uygulanacağını hakkında yönergeler için <xref:System.ComponentModel.TypeConverterAttribute>, bkz: [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>XAML olay işleyicisi öznitelik sözdizimine özel bir sınıf olayları için gereksinimleri  
 Olarak kullanılabilmesi için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olayı, olay, varsayılan bir oluşturucu destekleyen bir sınıfı üzerinde ortak bir olayı olarak sunulmalıdır veya üzerinde bir Özet sınıf burada olay türetilmiş sınıflar üzerinde erişilebilir. Yönlendirilmiş olay olarak kolayca kullanılması için [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay açık uygulamak `add` ve `remove` eklemek ve kaldırmak için işleyiciler yöntemleri [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olay imzası ve bu işleyicilerineiletmek<xref:System.Windows.UIElement.AddHandler%2A>ve <xref:System.Windows.UIElement.RemoveHandler%2A> yöntemleri. Bu yöntemleri ekleyin veya işleyicileri olayı iliştirildiği örneğinde yönlendirilmiş olay işleyici deposuna kaldırın.  
  
> [!NOTE]
>  Kullanarak doğrudan yönlendirilmiş olayları için işleyiciler kaydetmek mümkündür <xref:System.Windows.UIElement.AddHandler%2A>ve kasıtlı olarak değil tanımlamak için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] yönlendirilmiş olay gösteren olay. Bu genellikle olay işleyicileri ekleme için XAML öznitelik sözdizimi izin vermez ve sonuçta elde edilen sınıfınızın daha az saydam XAML görünümü bu tür özellikleri, sunacaktır nedeniyle önerilmez.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Yazma koleksiyon özellikleri  
 Bir koleksiyon türüne talepteki özellikleri koleksiyonuna eklenen nesneleri belirtmenize olanak tanıyan bir XAML sözdizimi içeriyor. Bu sözdiziminin iki önemli özelliklere sahiptir.  
  
-   Koleksiyon nesnesi nesne nesne öğesi sözdiziminde belirtilmesi gerekmez. Bir özelliği bir koleksiyon türü alır XAML'de belirtirken bu koleksiyon türünün varolup olmadığını örtük.  
  
-   Koleksiyon özelliği biçimlendirmede alt öğelerinin koleksiyonun üyeleri olmasını işlenir. Normalde, kodu erişim bir koleksiyonun üyelerini listesi/sözlük yöntemlerle gibi gerçekleştirilir `Add`, veya bir dizin oluşturucu. Ancak yöntemleri veya dizin oluşturucular XAML sözdizimini desteklemez (özel durum: XAML 2009 yöntemleri destekler, ancak XAML 2009 kullanarak olası WPF kullanımları kısıtlar; bkz [XAML 2009 dil özellikleri](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). Belli ki öğeleri ağacının oluşturmaya yönelik yaygın bir gereksinim koleksiyonlarıdır ve bildirim temelli XAML'de bu koleksiyonları doldurmak için bazı yol gerekiyor. Bu nedenle, bir koleksiyon özelliği alt öğelerinin koleksiyonu özellik türü değeri koleksiyona ekleme tarafından işlenir.  
  
 .NET Framework XAML hizmetlerinde uygulama ve bu nedenle WPF XAML işlemci bir koleksiyon özelliği nelerin oluşturduğunu için aşağıdaki tanımını kullanır. Özelliğin özellik türü şunlardan birini uygulamanız gerekir:  
  
-   Implements <xref:System.Collections.IList>.  
  
-   Implements <xref:System.Collections.IDictionary> veya genel eşdeğer (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Türetilen <xref:System.Array> (XAML dizilerde hakkında daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implements <xref:System.Windows.Markup.IAddChild> (tarafından tanımlanan bir arabirim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Her CLR içinde bu tür bir `Add` XAML işlemcisi tarafından Nesne grafiği oluştururken öğeleri temel koleksiyona eklemek için kullanılan yöntem.  
  
> [!NOTE]
>  Genel `List` ve `Dictionary` arabirimleri (<xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602>) koleksiyon algılama tarafından desteklenmeyen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci. Bununla birlikte, kullanabilirsiniz <xref:System.Collections.Generic.List%601> bunu uyguladığı için bir temel sınıf olarak sınıf <xref:System.Collections.IList> doğrudan veya <xref:System.Collections.Generic.Dictionary%602> bir temel sınıf olarak bunu uyguladığından <xref:System.Collections.IDictionary> doğrudan.  
  
 Bir koleksiyon alır bir özelliği bildirme, bu özellik değeri türü yeni örneklerini nasıl başlatılır hakkında dikkatli olun. Özelliği bir bağımlılık özelliği olarak uyguluyorsanız değil, toplama türü oluşturucuyu çağırır yedekleme alanını kullan özelliği olması yeterlidir. Ardından, özelliği, bir bağımlılık özelliği olan ise varsayılan tür Oluşturucu bir parçası olarak koleksiyon özelliği başlatmak gerekebilir. Bu bağımlılık özelliği meta verilerden varsayılan değerini alır ve genellikle bir statik, paylaşılan koleksiyonu olması için bir koleksiyon özelliği ilk değerini istiyor musunuz kaynaklanır. Her içeren türü örneği başına bir koleksiyon örnek olması gerekir. Daha fazla bilgi için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Koleksiyon özellik için özel koleksiyon türü uygulayabilirsiniz. Örtük koleksiyon özelliği kullanımı nedeniyle özel koleksiyon türü XAML'de örtük olarak kullanılması için varsayılan bir oluşturucu sağlamanız gerekmez. Ancak, toplama türü için varsayılan bir oluşturucu isteğe bağlı olarak sağlayabilir. Bu faydalı bir uygulama olabilir. Varsayılan bir oluşturucu sağlamadıkça koleksiyonu object öğesi olarak açıkça bildiremezsiniz. Bazı biçimlendirme yazarları açık koleksiyonu biçimlendirme stili sağlasa da, görmek tercih edebilirsiniz. Ayrıca, bir özellik değeri olarak, koleksiyon türü kullanan yeni nesneler oluşturduğunuzda varsayılan bir oluşturucu başlatma gereksinimleri basitleştirebilirsiniz.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>XAML İçerik özellikleri bildirme  
 Kavramı, XAML dili tanımlayan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik özelliği. Nesne sözdiziminde kullanılabilir her sınıf tam olarak bir XAML İçerik özelliğine sahip olabilir. Sınıfınız için XAML içerik özelliği bir özelliği bildirme uygulamak <xref:System.Windows.Markup.ContentPropertyAttribute> sınıf tanımının bir parçası olarak. Hedeflenen XAML içerik özelliği adını belirtin <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> öznitelik. Özelliği bir dize olarak ada göre değil bir yansıma yapısı gibi belirtilen <xref:System.Reflection.PropertyInfo>.  
  
 XAML içerik özelliği bir koleksiyon özelliği belirtebilirsiniz. Bu nesne öğesi bir veya daha fazla alt öğe, herhangi bir araya giren koleksiyon nesnesi öğeleri veya özellik öğesi etiketleri olmadan yapabildiği olabilir bu özellik için bir kullanım sonuçlanır. Bu öğelerden sonra XAML İçerik özelliğinin değeri olarak kabul edilir ve yedekleme koleksiyonu örneğine eklenir.  
  
 Özellik türü var olan bazı XAML İçerik özellikleri kullanmak `Object`. Bu temel alabilir özellik değerlerinin gibi içerik XAML sağlayan bir <xref:System.String> tek başvuru nesne değeri alma yanı sıra. Bu model izlerseniz, işleme olası türlerinin yanı sıra tür belirleme türünüz sorumludur. Sık karşılaşılan nedeni bir <xref:System.Object> içerik türü (varsayılan sunu işleme alır) bir dize nesne içeriğini ekleme hem basit bir araç desteği veya ekleme Gelişmiş bir yol nesne varsayılan olmayan sunu belirtir içeriği veya ek veriler.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>XAML seri hale getirme  
 Eğer gibi belirli senaryolarda, bir denetim yazarı, XAML'de oluşturulabilir herhangi bir nesne temsili de geri eşdeğer XAML işaretleme serileştirilmesi güvence altına almak isteyebilirsiniz. Seri hale getirme gereksinimleri, bu konudaki açıklanmamaktadır. Bkz: [kontrol yazma genel bakışı](../../../../docs/framework/wpf/controls/control-authoring-overview.md) ve [öğe ağacı ve Serileştirme](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [XAML Yükleme ve Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
