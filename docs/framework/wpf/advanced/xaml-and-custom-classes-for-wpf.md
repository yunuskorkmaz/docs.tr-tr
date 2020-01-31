---
title: XAML ve özel sınıflar
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 8dab7310826357d7fbe434002298032b8722e5b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744431"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF için XAML ve Özel Sınıflar
Ortak dil çalışma zamanı (CLR) çerçeveleri içinde uygulanan XAML, herhangi bir ortak dil çalışma zamanı (CLR) dilinde özel bir sınıf veya yapı tanımlama özelliğini destekler ve sonra XAML işaretlemesini kullanarak bu sınıfa erişebilir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]tanımlı türlerin ve özel türlerinizin bir karışımını, genellikle özel türleri bir XAML ad alanı öneki ile eşleyerek aynı biçimlendirme dosyasında kullanabilirsiniz. Bu konu, bir özel sınıfın XAML öğesi olarak kullanılabilmesi için karşılaması gereken gereksinimleri tartışır.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Uygulamalarda veya derlemelerde özel sınıflar  
 XAML 'de kullanılan özel sınıflar iki farklı şekilde tanımlanabilir: arka plan kod veya birincil [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamayı üreten diğer kod içinde ya da sınıf kitaplığı olarak kullanılan çalıştırılabilir veya DLL gibi ayrı bir derlemede sınıf olarak. Bu yaklaşımların her biri belirli avantajlar ve dezavantajlara sahiptir.  
  
- Bir sınıf kitaplığı oluşturmanın avantajı, bu tür özel sınıfların birçok farklı uygulama genelinde paylaşılabilmesi olabilir. Ayrı bir kitaplık Ayrıca uygulamaların sürüm oluşturma sorunlarının daha kolay denetimini kolaylaştırır ve hedeflenen sınıf kullanımının XAML sayfasında kök öğe olduğu bir sınıfı oluşturmayı basitleştirir.  
  
- Uygulamada özel sınıflar tanımlamanın avantajı, bu tekniğin görece hafif olması ve ana uygulama yürütülebilirinin ötesinde ayrı derlemeler tanılarken karşılaşılan dağıtım ve test sorunlarını en aza indirir.  
  
- Aynı veya farklı derlemede tanımlanmış olup olmadığı, özel sınıfların XAML 'de öğe olarak kullanılabilmesi için CLR ad alanı ve XML ad alanı arasında eşlenmesi gerekir. Bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML öğesi olarak özel bir sınıf için gereksinimler  
 Bir nesne öğesi olarak örneklenebilir olması için, sınıfınızın aşağıdaki gereksinimleri karşılaması gerekir:  
  
- Özel sınıfınız ortak olmalıdır ve varsayılan (parametresiz) bir ortak oluşturucuyu desteklemelidir. (Yapılar hakkında notlar için aşağıdaki bölüme bakın.)  
  
- Özel sınıfınız iç içe geçmiş bir sınıf olmamalıdır. İç içe geçmiş sınıflar ve genel CLR kullanımı sözdiziminde "nokta", ekli özellikler gibi diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve/veya XAML özellikleriyle karışır.  
  
 Nesne tanımınız, nesne öğesi söz dizimini etkinleştirmeye ek olarak, bu nesneyi değer türü olarak alan diğer tüm ortak özellikler için özellik öğesi söz dizimini da etkinleştirir. Bunun nedeni, nesnenin artık bir nesne öğesi olarak örneklenebilir ve bu tür bir özelliğin özellik öğesi değerini doldurabilirler.  
  
### <a name="structures"></a>Yapılar  
 Özel türler olarak tanımladığınız yapılar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 'de her zaman oluşturulabiliyor. Bunun nedeni, CLR derleyicilerinin tüm özellik değerlerini varsayılan değerlerine Başlatan bir yapı için örtük olarak parametresiz bir Oluşturucu yaratmaktır. Bazı durumlarda, varsayılan oluşturma davranışı ve/veya bir yapı için nesne öğesi kullanımı istenmez. Bunun nedeni, yapının değerler ve işlev kavramsal olarak kavramsal olarak doldurulmasının amaçlandığı, burada içerilen değerlerin birbirini dışlamalı yorumlamalar olabileceği ve bu nedenle özelliklerinden hiçbirinin ayarlanamaz olması olabilir. Bu tür bir yapıya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örnek <xref:System.Windows.GridLength>. Genellikle, bu tür yapılar, değerlerin öznitelik biçiminde ifade edileceği, örneğin farklı yorumlamalar veya yapı değerlerinin modlarını oluşturan dize kuralları kullanılarak bir tür dönüştürücüsü uygulamalıdır. Yapı Ayrıca, parametresiz bir Oluşturucu aracılığıyla kod oluşturma için benzer davranışları kullanıma sunmalıdır.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>XAML öznitelikleri olarak özel bir sınıfın özellikleri için gereksinimler  
 Özellikler bir değere göre bir türe (ilkel gibi) başvurmalıdır veya parametresiz bir oluşturucuya ya da XAML işlemcisinin erişebileceği ayrılmış bir tür dönüştürücüde bulunan tür için bir sınıf kullanır. CLR XAML uygulamasında XAML işlemcileri, dil temel temelleri için yerel destek aracılığıyla veya <xref:System.ComponentModel.TypeConverterAttribute> uygulama aracılığıyla bir tür ya da bir üyeye geçiş türü tanımlar.  
  
 Alternatif olarak, özelliği bir soyut sınıf türüne veya arabirimine başvurabilir. Soyut sınıflar veya arabirimler için, XAML ayrıştırma beklentisi, özellik değerinin arabirimini uygulayan pratik sınıf örnekleriyle veya soyut sınıftan türetilen türlerin örneklerinin doldurulması gerekir.  
  
 Özellikler soyut bir sınıfta bildirilemez, ancak yalnızca soyut sınıftan türetilmiş pratik sınıflarda ayarlanabilir. Bunun nedeni, sınıf için nesne öğesinin oluşturulması sınıfında Ortak parametresiz bir Oluşturucu gerektirmesidir.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter etkin öznitelik sözdizimi  
 Sınıf düzeyinde adanmış, öznitelikli tür dönüştürücüsü sağlarsanız, uygulanan tür dönüştürmesi, bu türü örneklemesi gereken herhangi bir özellik için öznitelik sözdizimini sağlar. Tür dönüştürücüsü nesnenin nesne öğesi kullanımını etkinleştirmez; Bu tür için yalnızca parametresiz bir oluşturucunun varlığı, nesne öğesi kullanımını mümkün. Bu nedenle, türün kendisi de nesne öğesi sözdizimini desteklemediği takdirde tür dönüştürücüsü etkin olan özellikler genellikle özellik sözdiziminde kullanılamaz. Bunun özel durumu, bir özellik öğesi söz dizimini belirtebileceğiniz, ancak Property öğesinin bir dize içermesi olabilir. Bu kullanım aslında bir öznitelik sözdizimi kullanımına eşdeğerdir ve öznitelik değerinin daha sağlam bir boşluk işlemesi olması gerekmediği takdirde bu kullanım yaygın değildir. Örneğin, aşağıdaki bir dize alan ve öznitelik kullanım eşdeğerini olan bir özellik öğesi kullanımdır:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Öznitelik sözdizimine izin verilen özelliklerin örnekleri, ancak XAML aracılığıyla nesne öğesi içeren özellik öğesi sözdizimine izin verilmez <xref:System.Windows.Input.Cursor> türü alan çeşitli özelliklerdir. <xref:System.Windows.Input.Cursor> sınıfı, <xref:System.Windows.Input.CursorConverter>özel bir tür dönüştürücüye sahiptir, ancak parametresiz bir Oluşturucu sunmaz, bu nedenle <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği yalnızca gerçek <xref:System.Windows.Input.Cursor> türü bir başvuru türü olsa bile öznitelik sözdizimi aracılığıyla ayarlanabilir.  
  
### <a name="per-property-type-converters"></a>Özellik başına tür dönüştürücüler  
 Alternatif olarak, özelliğinin kendisi de özellik düzeyinde bir tür dönüştürücüsü bildirebilir. Bu, özelliğin gelen dize değerlerini, uygun türe göre <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> bir işlem için girdi olarak işleyerek bir "Mini dil" özelliği sunar. Genellikle bu bir kullanışlı erişimci sağlamak için yapılır ve XAML 'de bir özelliği ayarlamayı etkinleştirmek için tek bir yöntem olarak değildir. Ancak, parametresiz bir Oluşturucu ya da öznitelikli tür dönüştürücüsü içermeyen mevcut CLR türlerini kullanmak istediğiniz öznitelikler için tür dönüştürücülerinin kullanılması da mümkündür. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API örnekleri, <xref:System.Globalization.CultureInfo> türünü alan bazı özelliklerdir. Bu durumda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Framework 'ün önceki sürümlerinde kullanılan uyumluluk ve geçiş senaryolarına daha iyi adres sağlamak için mevcut Microsoft .NET Framework <xref:System.Globalization.CultureInfo> türünü kullandı, ancak <xref:System.Globalization.CultureInfo> türü, doğrudan XAML özellik değeri olarak kullanılabilmesi için gerekli oluşturucuları veya tür düzeyi tür dönüştürmeyi desteklemez.  
  
 XAML kullanımına sahip bir özelliği kullanıma sunışınızda, özellikle bir denetim yazarlýşınızda, bu özelliği bir bağımlılık özelliği ile yedeklemeyi kesin bir şekilde dikkate almanız gerekir. Bu özellikle, XAML işlemcisinin mevcut [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamasını kullandığınızda geçerlidir çünkü <xref:System.Windows.DependencyProperty> Yedekleme kullanarak performansı geliştirebilirsiniz. Bağımlılık özelliği, özelliği için kullanıcıların XAML erişilebilir bir özelliği bekleecek şekilde özellik sistem özelliklerini kullanıma sunar. Bu, animasyon, veri bağlama ve stil desteği gibi özellikleri içerir. Daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md) ve [XAML yükleme ve bağımlılık özellikleri](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Tür dönüştürücüsü yazma ve Attributing  
 Bazen Özellik türü için tür dönüştürmesi sağlamak üzere özel <xref:System.ComponentModel.TypeConverter> türetilmiş bir sınıf yazmanız gerekir. ' Dan türeme ve XAML kullanımlarını destekleyebilen bir tür dönüştürücüsü oluşturma ve <xref:System.ComponentModel.TypeConverterAttribute>uygulama hakkında yönergeler için bkz. [TypeConverters ve xaml](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Özel bir sınıfın olaylarında XAML olay Işleyicisi öznitelik sözdizimi için gereksinimler  
 CLR olayı olarak kullanılabilmesi için, olayın parametresiz bir oluşturucuyu destekleyen bir sınıfta veya türetilmiş sınıflarda olaya erişilebilen bir soyut sınıfta, olay ortak olay olarak kullanıma sunulmalıdır. Yönlendirilmiş olay olarak kolayca kullanılabilmesi için, CLR olaylarınızın, CLR olay imzası için işleyicileri ekleyip kaldırarak ve bu işleyicileri <xref:System.Windows.UIElement.AddHandler%2A> ve <xref:System.Windows.UIElement.RemoveHandler%2A> yöntemlerine ileten açık `add` ve `remove` yöntemleri uygulaması gerekir. Bu yöntemler, etkinliğin eklendiği örnekteki yönlendirilmiş olay işleyicisi deposuna işleyicileri ekler veya kaldırır.  
  
> [!NOTE]
> <xref:System.Windows.UIElement.AddHandler%2A>kullanarak doğrudan yönlendirilmiş olaylara yönelik işleyicileri kaydetmek ve yönlendirilmiş olayı kullanıma sunan bir CLR olayını kasıtlı olarak tanımlamak mümkündür. Bu, genel olarak önerilmez çünkü olay, işleyicileri eklemek için XAML öznitelik sözdizimini etkinleştirmeyecektir ve elde edilen sınıfınız bu türün özelliklerine daha az saydam bir XAML görünümü sunacaktır.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Koleksiyon özellikleri yazılıyor  
 Koleksiyon türü alan özellikler, koleksiyona eklenen nesneleri belirtmenizi sağlayan bir XAML sözdizimine sahiptir. Bu sözdiziminin iki önemli özelliği vardır.  
  
- Koleksiyon nesnesi olan nesnenin nesne öğesi sözdiziminde belirtilmesi gerekmez. Bir koleksiyon türü alan XAML 'de bir özellik belirttiğinizde, bu koleksiyon türünün varlığı örtük bir şekilde gerçekleşir.  
  
- Biçimlendirme içindeki koleksiyon özelliğinin alt öğeleri, koleksiyonun üyesi olacak şekilde işlenir. Genellikle, bir koleksiyonun üyelerine yönelik kod erişimi, `Add`gibi liste/sözlük yöntemleri veya bir dizin oluşturucu aracılığıyla gerçekleştirilir. Ancak XAML sözdizimi yöntemleri veya dizin oluşturucuyu desteklemez (özel durum: XAML 2009 yöntemleri destekleyebilir, ancak XAML 2009 kullanmak olası WPF kullanımlarını kısıtlar; [xaml 2009 dil özelliklerine](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)bakın). Koleksiyonlar bir öğe ağacı oluşturmak için çok yaygın bir gereksinimdir ve bu koleksiyonları bildirime dayalı XAML 'de doldurmanız için bir yol gerekir. Bu nedenle, bir koleksiyon özelliğinin alt öğeleri, koleksiyon özelliği tür değeri olan koleksiyona eklenerek işlenir.  
  
 .NET Framework XAML Hizmetleri uygulamasını ve böylece WPF XAML işlemcisi, bir koleksiyon özelliğini oluşturan için aşağıdaki tanımı kullanır. Özelliğin özellik türü aşağıdakilerden birini gerçekleştirmelidir:  
  
- <xref:System.Collections.IList>uygular.  
  
- <xref:System.Collections.IDictionary> veya genel eşdeğerini uygular (<xref:System.Collections.Generic.IDictionary%602>).  
  
- <xref:System.Array> türetilir (XAML içindeki diziler hakkında daha fazla bilgi için bkz. [X:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
- <xref:System.Windows.Markup.IAddChild> uygular ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından tanımlanan bir arabirim).  
  
 CLR 'deki bu türlerin her biri, nesne grafiğini oluştururken temel koleksiyona öğe eklemek için XAML işlemcisi tarafından kullanılan bir `Add` yöntemine sahiptir.  
  
> [!NOTE]
> Genel `List` ve `Dictionary` arabirimleri (<xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602>), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemcisi tarafından koleksiyon algılama için desteklenmez. Ancak, doğrudan <xref:System.Collections.IDictionary> uyguladığından, <xref:System.Collections.IList> doğrudan veya temel sınıf olarak <xref:System.Collections.Generic.Dictionary%602> uyguladığından <xref:System.Collections.Generic.List%601> sınıfını temel sınıf olarak kullanabilirsiniz.  
  
 Bir koleksiyonu alan bir özellik bildirdiğinizde, bu özellik değerinin türün yeni örneklerinde nasıl başlatıldığıyla ilgili dikkatli olun. Özelliği bir bağımlılık özelliği olarak uygulamadıysanız, özelliğin koleksiyon türü oluşturucusunu çağıran bir yedekleme alanı kullanması yeterlidir. Eğer Eğer özelliği bir bağımlılık özelliği ise, koleksiyon özelliğini varsayılan tür oluşturucusunun bir parçası olarak başlatmak gerekebilir. Bunun nedeni, bağımlılık özelliğinin meta verilerden varsayılan değerini almaması ve genellikle bir koleksiyon özelliğinin başlangıçtaki değerinin statik, paylaşılan bir koleksiyon olmasını istemezsiniz. Her bir kapsayan tür örneği için bir koleksiyon örneği olmalıdır. Daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
 Koleksiyon özelliği için özel bir koleksiyon türü uygulayabilirsiniz. Örtük koleksiyon özelliği işlemi nedeniyle, özel koleksiyon türünün XAML 'de örtük olarak kullanılabilmesi için parametresiz bir Oluşturucu sağlamasına gerek yoktur. Ancak, isteğe bağlı olarak, koleksiyon türü için parametresiz bir Oluşturucu sağlayabilirsiniz. Bu bir Wora yöntemi olabilir. Parametresiz bir Oluşturucu sağlamadığınız sürece, koleksiyonu açıkça bir nesne öğesi olarak bildiremezsiniz. Bazı biçimlendirme yazarları, biçimlendirme stiliyle bağımsız olarak açık toplamayı görmeyi tercih edebilir. Ayrıca, parametresiz bir Oluşturucu, koleksiyon türünü bir özellik değeri olarak kullanan yeni nesneler oluşturduğunuzda başlatma gereksinimlerini basitleştirebilir.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>XAML Içerik özelliklerini bildirme  
 XAML dili [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir içerik özelliği kavramını tanımlar. Nesne sözdiziminde kullanılabilir olan her sınıf tam olarak bir XAML içerik özelliğine sahip olabilir. Sınıfınız için XAML içerik özelliği olarak bir özelliği bildirmek için, <xref:System.Windows.Markup.ContentPropertyAttribute> sınıf tanımının bir parçası olarak uygulayın. İstenen XAML içerik özelliğinin adını özniteliğinde <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> olarak belirtin. Özelliği, <xref:System.Reflection.PropertyInfo>gibi bir yansıma yapısı olarak değil, ada göre bir dize olarak belirtilir.  
  
 XAML içerik özelliği olarak bir koleksiyon özelliği belirtebilirsiniz. Bu, nesne öğesinin bir veya daha fazla alt öğesine sahip olması ve herhangi bir araya eklenen koleksiyon nesnesi öğesi ya da Özellik öğesi etiketleri olmadan bu özelliğin kullanılmasına neden olur. Bu öğeler daha sonra XAML içerik özelliği için değer olarak değerlendirilir ve yedekleme koleksiyonu örneğine eklenir.  
  
 Bazı var olan XAML içerik özellikleri `Object`Özellik türünü kullanır. Bu, <xref:System.String> gibi temel değerleri ve tek bir başvuru nesnesi değeri almayı sağlayan bir XAML içerik özelliği sunar. Bu modeli izlerseniz, tipiniz tür belirlemekten ve olası türlerin işlenmesinden sorumludur. <xref:System.Object> bir içerik türünün tipik nedeni, nesne içeriğini bir dize olarak (varsayılan bir sunum işlemi alır) veya varsayılan olmayan bir sunuyu veya ek verileri belirten gelişmiş nesne içeriği ekleme gibi basit bir şekilde desteklemek içindir.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>XAML serileştirme  
 Bir denetim yazarı gibi belirli senaryolarda, XAML 'de örneklenebilir herhangi bir nesne gösteriminin de eşdeğer XAML biçimlendirmesine geri serileştirilmesine emin olmak isteyebilirsiniz. Serileştirme gereksinimleri bu konuda açıklanmamaktadır. Bkz. [Denetim yazma genel bakış](../controls/control-authoring-overview.md) ve [öğe ağacı ve serileştirme](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
- [XAML Yükleme ve Bağımlılık Özellikleri](xaml-loading-and-dependency-properties.md)
