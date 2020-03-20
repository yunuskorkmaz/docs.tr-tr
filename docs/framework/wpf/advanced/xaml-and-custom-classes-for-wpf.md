---
title: XAML ve özel sınıflar
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 4cd0ba7fa03d2578f4477c3ccf53188fbbea2dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186259"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF için XAML ve Özel Sınıflar
Ortak dil çalışma zamanı (CLR) çerçevelerinde uygulandığı xaml, herhangi bir ortak dil çalışma zamanı (CLR) dilinde özel bir sınıf veya yapı tanımlama ve ardından XAML biçimlendirmesini kullanarak bu sınıfa erişme yeteneğini destekler. Genellikle özel türleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]xaml ad alanı önekiyle eşleyerek, aynı biçimlendirme dosyası içinde tanımlanmış türleri ve özel türleri karışımını kullanabilirsiniz. Bu konu, xaml öğesi olarak kullanılabilir olması için özel bir sınıfın karşılaması gereken gereksinimleri tartışır.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>
## <a name="custom-classes-in-applications-or-assemblies"></a>Uygulamalarda veya Derlemelerde Özel Sınıflar  
 XAML'de kullanılan özel sınıflar iki farklı şekilde tanımlanabilir: birincil [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamayı oluşturan kod arkası veya diğer kod içinde veya sınıf kitaplığı olarak kullanılan yürütülebilir veya DLL gibi ayrı bir derlemedeki sınıf olarak. Bu yaklaşımların her birinin belirli avantajları ve dezavantajları vardır.  
  
- Sınıf kitaplığı oluşturmanın avantajı, bu tür özel sınıfların birçok farklı olası uygulama arasında paylaşılmasıdır. Ayrı bir kitaplık, uygulamaların sürüm sorunlarını da denetlemeyi kolaylaştırır ve amaçlanan sınıf kullanımının XAML sayfasında kök öğe olarak olduğu bir sınıf oluşturmayı kolaylaştırır.  
  
- Uygulamadaki özel sınıfları tanımlamanın avantajı, bu tekniğin nispeten hafif olması ve çalıştırılabilir ana uygulamanın ötesinde ayrı derlemeler tanıttığınızda karşılaşılan dağıtım ve sınama sorunlarını en aza indirgemektir.  
  
- XAML'de öğe olarak kullanılabilmesi için, aynı veya farklı derlemede tanımlanmış olsun, özel sınıfların CLR ad alanı ile XML ad alanı arasında eşlemesi gerekir. [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşleme'ye](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML Öğesi Olarak Özel Sınıf Gereksinimleri  
 Bir nesne öğesi olarak anında alınabilmek için sınıfınızın aşağıdaki gereksinimleri karşılaması gerekir:  
  
- Özel sınıfınız herkese açık olmalı ve varsayılan (parametresiz) ortak oluşturucuyunuzu desteklemelidir. (Yapılarla ilgili notlar için aşağıdaki bölüme bakın.)  
  
- Özel sınıfınız iç içe bir sınıf olmamalıdır. İç içe sınıflar ve genel CLR kullanım sözdiziminde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yer alan "nokta", ekli özellikler gibi diğer ve/veya XAML özelliklerini bozar.  
  
 Nesne öğesi sözdizimini etkinleştirmeye ek olarak, nesne tanımınız, sözkonusu nesneyi değer türü olarak alan diğer ortak özellikler için özellik öğesi sözdizimini de etkinleştirirken. Bunun nedeni, nesnenin artık bir nesne öğesi olarak anlık olarak kullanılabilir ve böyle bir özelliğin özellik öğesi değerini doldurabilir olmasıdır.  
  
### <a name="structures"></a>Yapılar  
 Özel türler olarak tanımladığınız yapılar her zaman XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde oluşturulabilir. Bunun nedeni, CLR derleyicilerinin tüm özellik değerlerini varsayılanlarına göre başharfleyen bir yapı için dolaylı olarak parametresiz bir oluşturucu oluşturmasıdır. Bazı durumlarda, bir yapı için varsayılan yapı davranışı ve/veya nesne öğesi kullanımı istenmez. Bunun nedeni, yapının değerleri doldurmak ve kavramsal olarak bir birlik olarak işlev görmek için tasarlanmış olması, içerdiği değerlerin birbirini dışlayan yorumları olabilir ve bu nedenle özelliklerinin hiçbirinin ayarlanamayan olması olabilir. Böyle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir yapıya <xref:System.Windows.GridLength>örnek olarak . Genel olarak, bu tür yapılar, yapıdeğerlerinin farklı yorumlarını veya modlarını oluşturan dize kuralları kullanarak, değerlerin öznitelik formunda ifade edilebildiği bir tür dönüştürücü uygulamalıdır. Yapı da parametresiz olmayan bir oluşturucu aracılığıyla kod oluşturma için benzer davranış ortaya çıkarmalıdır.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>XAML Öznitelikleri olarak Özel Bir Sınıfın Özellikleri Için Gereksinimler  
 Özellikler bir yan değer türüne (ilkel gibi) başvurmalı veya parametresiz bir oluşturucuya veya XAML işlemcinin erişebileceği özel bir tür dönüştürücüse sahip bir tür için bir sınıf kullanmalıdır. CLR XAML uygulamasında, XAML işlemciler bu tür dönüştürücüleri ya dil ilkelleri <xref:System.ComponentModel.TypeConverterAttribute> için yerel destek yoluyla ya da destek türü tanımlarında bir türe veya üyeye uygulama yoluyla bulurlar  
  
 Alternatif olarak, özellik soyut bir sınıf türüne veya arabirime başvurabilir. Soyut sınıflar veya arabirimler için XAML ayrıştırma beklentisi, özellik değerinin arabirimi uygulayan pratik sınıf örnekleri veya soyut sınıftan tür örnekleriyle doldurulması dır.  
  
 Özellikler soyut bir sınıfta bildirilebilir, ancak yalnızca soyut sınıftan türeyen pratik sınıflara ayarlanabilir. Bunun nedeni, sınıf için nesne öğesini oluşturmanın sınıfta ortak parametresiz bir oluşturucu gerektirmesidir.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter Etkin Öznitelik Sözdizimi  
 Sınıf düzeyinde özel, atfedilen bir tür dönüştürücü sağlarsanız, uygulanan tür dönüştürme, bu türü anında alması gereken herhangi bir özellik için öznitelik sözdizimini sağlar. Bir tür dönüştürücü türün nesne öğesi kullanımını etkinleştirmez; yalnızca bu tür için parametresiz bir oluşturucunun varlığı nesne öğesi kullanımını sağlar. Bu nedenle, tür dönüştürücü etkin olan özellikler genellikle özellik sözdiziminde kullanılabilir değil, tür kendisi de nesne öğesi sözdizimini desteklemediği sürece konuşuyor. Bunun istisnası, bir özellik öğesi sözdizimi belirtebilmek, ancak özellik öğesi bir dize içermelidir. Bu kullanım gerçekten bir öznitelik sözdizimi kullanımına eşdeğerdir ve öznitelik değerinin daha sağlam beyaz alan işlemesi için bir ihtiyaç olmadığı sürece böyle bir kullanım yaygın değildir. Örneğin, aşağıdaki bir dize alan bir özellik öğesi kullanımı ve öznitelik kullanım eşdeğeri:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Öznitelik sözdizimine izin verilen ancak nesne öğesi içeren özellik öğesi sözdiziminin XAML aracılığıyla <xref:System.Windows.Input.Cursor> izin verilmediği özellikler örnekleri, türü alan çeşitli özelliklerdir. Sınıfın <xref:System.Windows.Input.Cursor> özel bir tür <xref:System.Windows.Input.CursorConverter>dönüştürücüsü vardır, ancak parametresiz <xref:System.Windows.FrameworkElement.Cursor%2A> bir oluşturucu ortaya çıkarmaz, bu nedenle <xref:System.Windows.Input.Cursor> özellik yalnızca gerçek tür bir başvuru türü olsa bile öznitelik sözdizimi ile ayarlanabilir.  
  
### <a name="per-property-type-converters"></a>Özellik Başına Tip Dönüştürücüler  
 Alternatif olarak, özelliğin kendisi özellik düzeyinde bir tür dönüştürücü bildirebilir. Bu, özniteliğin gelen dize değerlerini uygun türe dayalı bir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> işlem girişi olarak işleyerek, özellik satır içinde olan nesnelerini anında anımsa bir "mini dil" sağlar. Genellikle bu, XAML'de bir özellik ayarlamayı etkinleştirmek için tek araç olarak değil, kolaylık sağlayan bir erişimaracı sağlamak için yapılır. Ancak, parametresiz bir oluşturucu veya atfedilen tür dönüştürücü kaynağı olmayan varolan CLR türlerini kullanmak istediğiniz öznitelikler için tür dönüştürücüleri kullanmak da mümkündür. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'den örnekler, <xref:System.Globalization.CultureInfo> türü alan belirli özelliklerdir. Bu durumda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çerçevelerin önceki sürümlerinde kullanılan uyumluluk ve geçiş senaryolarını daha iyi adreslemek için varolan Microsoft .NET Framework <xref:System.Globalization.CultureInfo> türü kullanılmıştır, ancak <xref:System.Globalization.CultureInfo> tür, doğrudan XAML özellik değeri olarak kullanılabilir olması için gerekli oluşturucuları veya tür düzeyi türü dönüştürmeyi desteklemedi.  
  
 XAML kullanımı olan bir özelliği ortaya çıkardığında, özellikle bir denetim yazarıysanız, bu özelliği bağımlılık özelliğiyle desteklemeyi güçlü bir şekilde düşünmelisiniz. Bu, özellikle XAML işlemcinin varolan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamasını kullanıyorsanız doğrudur, çünkü <xref:System.Windows.DependencyProperty> desteği kullanarak performansı artırabilirsiniz. Bağımlılık özelliği, kullanıcıların XAML erişilebilir bir özellik için beklediğiniz özellik sistemi özelliklerini ortaya çıkaracaktır. Bu, animasyon, veri bağlama ve stil desteği gibi özellikleri içerir. Daha fazla bilgi için bkz: [Özel Bağımlılık Özellikleri](custom-dependency-properties.md) ve [XAML Yükleme ve Bağımlılık Özellikleri.](xaml-loading-and-dependency-properties.md)  
  
### <a name="writing-and-attributing-a-type-converter"></a>Bir Tür Dönüştürücü Yazma ve Atfetme  
 Bazen özellik türünüz için <xref:System.ComponentModel.TypeConverter> tür dönüştürme sağlamak için özel türetilmiş bir sınıf yazmanız gerekir. XAML kullanımlarını destekleyebilen bir tür dönüştürücüden nasıl türetilebileceği ve <xref:System.ComponentModel.TypeConverterAttribute>nasıl uygulanacağı ile ilgili talimatlar için [TypeConverters ve XAML'ye](typeconverters-and-xaml.md)bakın.  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Özel Sınıfın Olaylarında XAML Olay İşleyicisi Özniteliği Sözdizimi Gereksinimleri  
 BIR CLR olayı olarak kullanılabilir olması için, olayın parametresiz bir oluşturucuyu destekleyen bir sınıfta veya olaytüretilen sınıflarda erişilebilen soyut bir sınıfta herkese açık bir olay olarak ortaya konması gerekir. Yönlendirilen bir olay olarak rahatlıkla kullanılabilmesi için, CLR `add` `remove` etkinliğiniz, CLR olay imzası için işleyicileri ekleyip kaldıran <xref:System.Windows.UIElement.AddHandler%2A> ve <xref:System.Windows.UIElement.RemoveHandler%2A> bu işleyicileri ve yöntemlere ileten açık ve yöntemleri uygulamalıdır. Bu yöntemler, işleyicileri olayın bağlı olduğu örnekte yönlendirilen olay işleyicisi deposuna ekler veya kaldırır.  
  
> [!NOTE]
> İşleyicileri doğrudan yönlendirilen olaylar <xref:System.Windows.UIElement.AddHandler%2A>için kaydetmek ve yönlendirilen olayı ortaya çıkaran bir CLR olayını kasıtlı olarak tanımlamamak mümkündür. Olay işleyicileri eklemek için XAML öznitelik sözdizimini etkinleştirmez ve ortaya çıkan sınıf bu tür yeteneklerini daha az saydam bir XAML görünümü sunacak, çünkü bu genellikle önerilmez.  
  
<a name="Collection_Properties"></a>
## <a name="writing-collection-properties"></a>Toplama Özelliklerini Yazma  
 Koleksiyon türü alan özellikleri, koleksiyona eklenen nesneleri belirtmenizi sağlayan bir XAML sözdizimi içerir. Bu sözdizimi nin iki önemli özelliği vardır.  
  
- Koleksiyon nesnesi olan nesnenin nesne öğesi sözdiziminde belirtilmesi gerekmez. XAML'de bir koleksiyon türü alan bir özellik belirttiğiniz de, bu koleksiyon türünün varlığı örtülüdür.  
  
- Biçimlendirmedeki koleksiyon özelliğinin alt öğeleri, koleksiyona üye olmak için işlenir. Normalde, bir koleksiyonun üyelerine kod erişimi, liste/sözlük yöntemleri yle `Add`veya bir dizin leyici aracılığıyla gerçekleştirilir. Ancak XAML sözdizimi yöntemleri veya dizinleyicileri desteklemez (özel durum: XAML 2009 yöntemleri destekleyebilir, ancak XAML 2009'u kullanmak olası WPF kullanımlarını kısıtlar; [bkz.](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md) Koleksiyonlar açıkça bir öğe ağacı oluşturmak için çok yaygın bir gerekliliktir ve bildirimsel XAML bu koleksiyonları doldurmak için bir yol gerekir. Bu nedenle, bir koleksiyon özelliğinin alt öğeleri, koleksiyon özelliği türü değeri olan koleksiyona eklenerek işlenir.  
  
 .NET Framework XAML Services uygulaması ve böylece WPF XAML işlemci, bir toplama özelliğini oluşturan şey için aşağıdaki tanımı kullanır. Özelliğin özellik türü aşağıdakilerden birini uygulamalıdır:  
  
- Uygular. <xref:System.Collections.IList>  
  
- Uygular <xref:System.Collections.IDictionary> veya genel eşdeğeri (<xref:System.Collections.Generic.IDictionary%602>).  
  
- Türetilir <xref:System.Array> (XAML'deki diziler hakkında daha fazla bilgi için [bkz. x:Dizi Biçimlendirme Uzantısı](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
- Uygular <xref:System.Windows.Markup.IAddChild> (tarafından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tanımlanan bir arayüz).  
  
 CLR'deki bu türlerin `Add` her birinin, nesne grafiği oluşturulurken temel koleksiyona öğe eklemek için XAML işlemcisi tarafından kullanılan bir yöntemi vardır.  
  
> [!NOTE]
> Genel `List` ve `Dictionary` arabirimler<xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IDictionary%602>( ve ) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci tarafından toplama algılama için desteklenmez. Ancak, <xref:System.Collections.Generic.List%601> sınıfı doğrudan veya doğrudan uygulandığıiçin <xref:System.Collections.IList> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.IDictionary> taban sınıf olarak veya taban sınıf olarak kullanabilirsiniz.  
  
 Bir koleksiyon alan bir özelliği beyan ettiğinizde, bu özellik değerinin türün yeni örneklerinde nasıl başharfe başlatı edildiği konusunda dikkatli olun. Özelliği bağımlılık özelliği olarak uygulamıyorsanız, özelliğin toplama türü oluşturucuyu çağıran bir destek alanı kullanmasını n için yeterlidir. Özelliğiniz bir bağımlılık özelliğiyse, varsayılan tür oluşturucunun bir parçası olarak toplama özelliğini başlatmanız gerekebilir. Bunun nedeni, bağımlılık özelliğinin varsayılan değerini meta verilerden alması ve genellikle bir koleksiyon özelliğinin ilk değerinin statik, paylaşılan bir koleksiyon olmasını istememenizdir. Her tür örneği içeren bir toplama örneği olmalıdır. Daha fazla bilgi için [bkz.](custom-dependency-properties.md)  
  
 Koleksiyon özelliğiniz için özel bir koleksiyon türü uygulayabilirsiniz. Örtük toplama özelliği işleme nedeniyle, özel toplama türü xaml örtülü olarak kullanılmak üzere parametresiz bir yapıcı sağlamak gerekmez. Ancak, isteğe bağlı olarak koleksiyon türü için parametresiz bir oluşturucu sağlayabilirsiniz. Bu değerli bir uygulama olabilir. Parametresiz bir oluşturucu sağlamadığınız sürece, koleksiyonu açıkça nesne öğesi olarak bildiremezsiniz. Bazı biçimlendirme yazarları açık koleksiyonu biçimlendirme stili olarak görmeyi tercih edebilir. Ayrıca, parametresiz bir oluşturucu, koleksiyon türünüzü özellik değeri olarak kullanan yeni nesneler oluşturduğunuzda başlatma gereksinimlerini basitleştirebilir.  
  
<a name="XAMLCONtent"></a>
## <a name="declaring-xaml-content-properties"></a>XAML İçerik Özelliklerini Bildirme  
 XAML dili [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik özelliği kavramını tanımlar. Nesne sözdiziminde kullanılabilir her sınıf tam olarak bir XAML içerik özelliğine sahip olabilir. Bir özelliği sınıfınız için XAML içerik özelliği olarak <xref:System.Windows.Markup.ContentPropertyAttribute> bildirmek için, bu özelliği sınıf tanımının bir parçası olarak uygulayın. Öznitelikte amaçlanan XAML içerik <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> özelliğinin adını belirtin. Özellik, yansıma yapısı olarak <xref:System.Reflection.PropertyInfo>değil, ada göre bir dize olarak belirtilir.  
  
 XAML içerik özelliği olacak bir koleksiyon özelliği belirtebilirsiniz. Bu, nesne öğesinin herhangi bir koleksiyon nesnesi öğesi veya özellik öğesi etiketleri müdahale etmeden bir veya daha fazla alt öğeye sahip olabileceği bu özellik için bir kullanımla sonuçlanır. Bu öğeler daha sonra XAML içerik özelliği için değer olarak kabul edilir ve destek toplama örneğine eklenir.  
  
 Bazı varolan XAML içerik özellikleri `Object`özelliği türünü kullanır. Bu, tek bir başvuru nesnesi değeri almanın <xref:System.String> yanı sıra a gibi ilkel değerleri de alabilen bir XAML içerik özelliği sağlar. Bu modeli izlerseniz, türünüzün yanı sıra olası türlerin işlenmesinden de sorumlu olur. <xref:System.Object> İçerik türünün tipik nedeni, hem nesne içeriğini bir dize olarak eklemenin basit bir aracını (varsayılan sunu işlemesi alır) hem de varsayılan olmayan bir sunu veya ek veri belirten nesne içeriği eklemenin gelişmiş bir aracını desteklemektir.  
  
<a name="Serializing"></a>
## <a name="serializing-xaml"></a>XAML'yi Serileştirme  
 Bir denetim yazarıysanız, XAML'de anlık olarak alınabilen herhangi bir nesne gösteriminin de eşdeğer XAML biçimlendirmesine geri serileştirilebilmesini sağlamak isteyebilirsiniz. Serileştirme gereksinimleri bu konuda açıklanmaz. Bkz. [Denetim Yazma Genel Bakış](../controls/control-authoring-overview.md) ve [Eleman Ağacı ve Serileştirme](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
- [XAML Yükleme ve Bağımlılık Özellikleri](xaml-loading-and-dependency-properties.md)
