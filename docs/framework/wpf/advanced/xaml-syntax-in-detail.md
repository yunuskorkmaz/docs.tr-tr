---
title: "Ayrıntılı XAML Sözdizimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88e66210fd8066e82a11d07ea0cfeb83808d646c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-syntax-in-detail"></a>Ayrıntılı XAML Sözdizimi
Bu konuda XAML sözdizimi öğeleri tanımlamak için kullanılan terimleri tanımlar. Bu koşulları sık bu belge, WPF belgeleri için her ikisini de geri kalanı boyunca özellikle ve XAML ya da XAML dil desteği System.Xaml düzeyinde etkinleştirilir temel XAML kavramları kullanan diğer çerçeveleri için kullanılır. Konu başlığı altında tanıtılan temel terimler bu konuda genişletir. [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML dil belirtimi  
 Burada tanımlanan XAML sözdizimi terminolojisi ayrıca tanımlı ya da XAML dil belirtimi içinde başvurulan. XAML XML tabanlı bir dildir ve izleyen veya XML yapısal kuralları temel genişletir. Bazı terminoloji paylaşılan veya XML dili veya XML belge nesnesi modeli açıklanırken yaygın olarak kullanılan terminolojiyi dayanır.  
  
 XAML dil belirtimi hakkında daha fazla bilgi için indirme [ \[MS XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525) Microsoft Download Center gelen.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML ve CLR  
 XAML biçimlendirme dilidir. [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], Etkinleştirir çalışma zamanı yürütme adını kullanarak örtük. XAML kendisi tarafından doğrudan CLR çalışma zamanı tarafından tüketilen yaygın diller biri değil. Bunun yerine, XAML kendi tür sistemi destek olarak düşünebilirsiniz. WPF tarafından kullanılan belirli XAML ayrıştırma system CLR ve CLR türü sistem üzerinde oluşturulmuştur. XAML türleri WPF XAML ayrıştırıldığında bir çalışma zamanı gösterimi örneği oluşturmak için CLR türlerine eşlenir. XAML dil belirtimi eşdeğer sözdizimi tartışmalara gerekmese bile bu nedenle, bu belgede söz dizimi tartışması geri kalanı CLR tür sistemi başvurular içerir. (XAML dil belirtimi düzeyi XAML türleri, CLR olması gerekmez, ancak, oluşturulmasını ve farklı bir XAML ayrıştırıcısı kullanımını gerektiren herhangi diğer türü sisteme eşleştirilebilir.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Üyeleri türleri ve sınıf devralma  
 Özellikleri ve olayları XAML üye olarak görünür olarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türü genellikle temel türlerden devralınmış. Örneğin, bu örneği göz önünde bulundurun: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> Özelliği değil hemen bildirilen bir özellik üzerinde <xref:System.Windows.Controls.Button> sınıf tanımı, yansıma sonuçları veya belgeleri aramak için olsaydı, sınıf. Bunun yerine, <xref:System.Windows.Controls.Control.Background%2A> taban devralınan <xref:System.Windows.Controls.Control> sınıfı.  
  
 Sınıf devralma davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML öğedir XML Biçimlendirme şeması tarafından zorlanan yorumu alanından önemli ölçüde. Sınıf devralma özellikle Ara temel sınıflarının soyut olduğunda veya arabirimleri söz konusu olduğunda karmaşık hale gelebilir. Tipik olarak kullanılan XAML öğeleri ve izin verilen öznitelikleri kümesini doğru şekilde ve tamamen şema türlerini kullanarak temsil etmek zor olan bir neden de budur [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , DTD ya da XSD biçimi gibi programlama. Başka bir nedeni, genişletilebilirlik ve izin verilen türleri ve üyeleri sabit herhangi gösterimini tamlığını XAML dili türü eşleme özelliklerini engellemek.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Nesne öğesi sözdizimi  
 *Nesne öğesi sözdizimi* bir XML öğesi bildirerek CLR sınıf veya yapı başlatır XAML biçimlendirme sözdizimi aşağıdaki gibidir. Bu sözdiziminin HTML gibi diğer biçimlendirme dilleri öğesi söz dizimi benzer. Nesne öğesi sözdizimi Sol açılı ayraç ile başlar (\<), ardından hemen sınıf veya yapı oluşturulmasını türü adı. Sıfır veya daha fazla boşluk tür adının takip edebilir ve sıfır veya daha fazla öznitelikler de bildirilen nesnesi öğesinde her öznitelik adı ayırarak bir veya daha fazla boşluk "value" eşleştirmesi. Son olarak, aşağıdakilerden biri doğru olmalıdır:  
  
-   Öğesini ve etiket sağ açılı ayraç (>) tarafından hemen ardından bir eğik çizgi (/) tarafından kapatılması gerekir.  
  
-   Açılış etiketi sağ açılı ayraç (>) tarafından tamamlanması gerekir. Diğer nesne öğeleri, özellik öğelerini veya iç metni açılış etiketi izleyebilirsiniz. Tam olarak hangi içerik burada yer alabilecek genellikle öğesi nesne modeli tarafından sınırlanır. Kapanış etiketi object öğesi için eşdeğer Ayrıca, uygun iç içe geçme var ve diğer açma ve kapatma etiketi çiftiyle dengelemeniz gerekir.  
  
 .NET tarafından uygulandığı gibi XAML türlerine, özellikleri veya olayları ve CLR ad alanları artı derleme için XAML ad uzayları öznitelikler nesne öğeleri eşleme kuralları kümesi vardır. WPF ve .NET Framework için XAML nesne öğeleri Eşle [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] tanımlandığı şekilde türleri başvurulan derlemeler ve bu türlerde üyelerine harita öznitelikleri. XAML'de bir CLR türü başvuru yaptığınızda, devralınan üyeleri türü de erişebilirsiniz.  
  
 Örneğin, aşağıdaki örnek yeni bir örneğini başlatır nesne öğesi sözdizimi <xref:System.Windows.Controls.Button> sınıfı ve ayrıca belirten bir <xref:System.Windows.FrameworkElement.Name%2A> özniteliği ve bu öznitelik için bir değer:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 XAML içerik özelliği sözdizimi de içeren nesne öğesi sözdizimi örnektir. İçinde yer alan iç metni ayarlamak için kullanılan <xref:System.Windows.Controls.TextBox> XAML içerik özelliği, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>İçerik modelleri  
 Bir sınıf bir kullanım XAML nesne öğesi sözdizimi açısından olarak desteklemiyor olabilir, ancak genel içerik modeli veya öğenin ağaç beklenen bir konumda yerleştirildiğinde bu öğe yalnızca bir uygulama veya sayfa düzgün. Örneğin, bir <xref:System.Windows.Controls.MenuItem> genellikle yalnızca bir alt öğesi olarak yerleştirilmelidir bir <xref:System.Windows.Controls.Primitives.MenuBase> türetilmiş sınıf gibi <xref:System.Windows.Controls.Menu>. İçerik modelleri belirli öğeler için denetimleri ve diğer sınıf sayfalarındaki açıklamalar bir parçası olarak belgelenmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML öğeleri olarak kullanılan sınıflar.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Nesne öğelerin özellikleri  
 XAML'de özellikleri olası sözdizimleri çeşitli tarafından ayarlanır. Hangi sözdizimi, belirli bir özellik için kullanılabilir, ayarladığınız özelliğin temel alınan tür sistem özelliklerine göre değişir.  
  
 Çalışma zamanında nesne grafiğinde oldukları gibi özelliklerinin değerlerini ayarlayarak, özellikleri veya özellikleri nesnelere ekleyin. Bir nesne öğesinden oluşturulan nesnenin ilk durumuna varsayılan oluşturucusu davranış temel alır. Genellikle, uygulamanızın tümüyle varsayılan örneği verilen herhangi bir nesnenin dışında bir şey kullanır.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (Özellikler)  
 Öznitelik sözdizimi bir özniteliği var olan bir nesne öğede bildirerek bir özellik için bir değer ayarlar XAML biçimlendirme sözdizimi şeklindedir. Öznitelik adı ilgili nesne öğesi yedekler sınıfı özelliğin CLR üye adı eşleşmelidir. Öznitelik adı atama işleci (=) izler. Öznitelik değeri tırnak alınmış bir dize olmalıdır.  
  
> [!NOTE]
>  Değişmez değer tırnak işareti içinde bir öznitelik yerleştirmek için alternatif teklifleri kullanabilirsiniz. Örneği için bir araç olarak tek tırnak içindeki çift tırnak karakteri içeren bir dize bildirmek için kullanabilirsiniz. Tek veya çift tırnak kullanıp kullanmayacağınızı eşleşen çifti açma ve kapama öznitelik değeri dizesi için kullanmanız gerekir. Ayrıca vardır kaçış dizileri veya diğer teknikleri belirli XAML söz dizimi uygulanan karakter kısıtlamaları çözümüne kullanılabilir. Bkz: [XML karakter varlıkları ve XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 Öznitelik sözdizimi ayarlamak için bir özellik genel olmalıdır ve yazılabilir olması gerekir. Örneği veya ilgili erişirken XAML işlemcisi tarafından başvurulan bir başvuru türü türü yedekleme gerekir veya yedekleme türü sistemindeki özelliğinin değeri bir değer türü olmalıdır.  
  
 WPF XAML olaylar için öznitelik adı başvurulan olay genel ve genel temsilci olması gerekir.  
  
 Özellik veya olay sınıfı veya içeren nesne öğesi tarafından örneği yapısı bir üyesi olması gerekir.  
  
### <a name="processing-of-attribute-values"></a>Öznitelik değerlerinin işlenmesi  
 Açılış ve kapanış tırnak işareti içinde yer alan dize değeri bir XAML işlemcisi tarafından işlenir. Özellikler için varsayılan davranış işleme altta yatan CLR özelliği türüne göre belirlenir.  
  
 Öznitelik değeri aşağıdakilerden biri tarafından girilir bu işleme sırası kullanarak:  
  
1.  XAML işlemci kaşlı ayraç veya türetilen nesne öğesindeki karşılaşırsa <xref:System.Windows.Markup.MarkupExtension>ardından değeri bir dize olarak işleme yerine ilk başvurulan biçimlendirme uzantısı değerlendirilir ve biçimlendirme uzantısı tarafından döndürülen nesne olarak kullanılır değer. Çoğu durumda biçimlendirme uzantısı tarafından döndürülen nesne var olan bir nesne ya da Değerlendirme çalışma zamanında kadar erteler ve yeni oluşturulmuş bir nesne değil bir ifade başvuru olacaktır.  
  
2.  Özellik bildirilirse bir öznitelikli ile <xref:System.ComponentModel.TypeConverter>, ya da özellik değeri türü bildirilmiş bir öznitelikli ile <xref:System.ComponentModel.TypeConverter>öznitelik dize değeri türü dönüştürücü dönüştürme giriş olarak gönderilir ve dönüştürücü döndürülecek bir Yeni nesne örneği.  
  
3.  Varsa hiçbir <xref:System.ComponentModel.TypeConverter>, özellik türü için doğrudan dönüştürme denenir. XAML dil ilkel türler veya adlandırılmış sabitler (sonra erişir eşleşen değerleri ayrıştırıcı) numaralandırma Adları Denetle arasında ayrıştırıcı yerel değerde doğrudan dönüştürme bu son düzeydir.  
  
#### <a name="enumeration-attribute-values"></a>Numaralandırma öznitelik değerleri  
 XAML'de numaralandırmalar doğası gereği XAML ayrıştırıcıları tarafından işlenir ve sabit adlandırılmış sabitler birinin dize adını belirterek bir numaralandırma üyeleri belirtilmelidir.  
  
 Nonflag numaralandırma değerleri için yerel bir öznitelik değeri dize işlemek ve numaralandırma değerlerinden biri olarak çözümlemek için bir davranıştır. Numaralandırma biçiminde belirtmeyin *numaralandırma*. *Değer*kodunda yaptığınız gibi. Bunun yerine, yalnızca belirttiğiniz *değeri*, ve *numaralandırma* ayarladığınızdan özelliğinin türü tarafından algılanır. Bir öznitelik belirtirseniz *numaralandırma*. *Değer* form, onu çözümlenmiyor doğru.  
  
 Davranış dayanır flagwise sabit listeleri için <xref:System.Enum.Parse%2A?displayProperty=nameWithType> yöntemi. Her değeri virgülle ayırarak flagwise numaralandırması için birden çok değer belirtebilirsiniz. Ancak, flagwise olmayan numaralandırma değerlerinin birleştiremez. Oluşturma denemesi için virgülle sözdizimi örneği için kullanamazsınız bir <xref:System.Windows.Trigger> nonflag numaralandırma birden çok koşul üzerinde çalışır:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML'de ayarlanabilir öznitelikleri destek flagwise numaralandırmalar WPF'de seyrek kullanılır. Ancak, bu tür bir numaralandırma olduğu <xref:System.Windows.Media.StyleSimulations>. Örneğin, virgülle ayrılmış flagwise öznitelik sözdizimi açıklamalar için sağlanan örnek değiştirmek için kullanabilirsiniz <xref:System.Windows.Documents.Glyphs> sınıfı; `StyleSimulations = "BoldSimulation"` hale gelebilir `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>Burada birden fazla numaralandırma değeri belirtilebilir başka bir özelliktir. Ancak, bu özellik özel bir durum olabilir çünkü olacağını <xref:System.Windows.Input.ModifierKeys> numaralandırma kendi türü dönüştürücü destekler. Değiştiriciler için tür dönüştürücüsünü ayırıcı virgül (,) yerine bir artı işareti (+) kullanır. Bu dönüştürme "Ctrl + Alt" gibi Microsoft Windows programlamada tuş bileşimlerini temsil etmek için daha geleneksel sözdizimini destekler.  
  
### <a name="properties-and-event-member-name-references"></a>Özellikler ve olay üye adı başvuruları  
 Bir öznitelik belirtirken, herhangi bir özelliği veya içeren nesne öğesi için örneği CLR türünün bir üyesi olarak mevcut olay başvuruda bulunabilir.  
  
 Veya iliştirilmiş bir Özellik Başvurusu yapabilir veya ekli olayı, içeren nesnenin öğesinin bağımsız. (Ekli özellikler ilerideki bölümde ele alınmıştır.)  
  
 Herhangi bir olay kullanarak varsayılan ad alanı aracılığıyla erişilebilen herhangi bir nesneden adının da bir *typeName*. *olay* kısmen tam adı; yönlendirilmiş olay işleyicileri ekleme destekler alt öğelerini, ancak üst öğenin yönlendirme olayları işlemek için işleyici burada hedeflenen de yok olay üyeler tablosunda bu sözdizimi. Bu sözdiziminin ekli olay sözdizimi benzer, ancak burada olayı true ekli olay değil. Bunun yerine, bir olay adıyla bir başvuruda bulunuyor. Daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Bazı senaryolarda, özellik adları bazen öznitelik adı yerine bir öznitelik değeri olarak sağlanır. Bu özellik adı biçiminde belirtilen özellik gibi niteleyicileri da içerebilir *ownerType*. *dependencyPropertyName*. Bu senaryo, stilleri veya şablonları XAML'de yazılırken yaygındır. Öznitelik değeri olarak sağlanan özellik adları için işleme kuralları farklıdır ve ayarlanan özelliğin türünü veya belirli WPF alt sistemleri davranışlarını tarafından yönetilir. Ayrıntılar için bkz [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Özellik adları için başka bir kullanım, bir öznitelik değeri özellik özelliğini ilişkiyi tanımlayan durumdur. Bu özellik film şeridi hedefleri ve veri bağlama için kullanılır ve etkin <xref:System.Windows.PropertyPath> sınıfı ve onun türü dönüştürücü. Arama semantikleri daha eksiksiz bir açıklaması için bkz: [PropertyPath XAML sözdizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Özellik öğesi sözdizimi  
 *Özellik öğesi sözdizimini* biraz öğeleri için temel XML sözdizimi kurallarına kareninkinden bir sözdizimi aşağıdaki gibidir. XML, gerçek bir dizeyi bir öznitelik değeri, yalnızca olası varyasyonuyla hangi dize kodlama biçimi kullanılıyor olması. XAML içinde bir özellik değeri olması için diğer nesne öğeleri atayabilirsiniz. Bu özellik, özellik öğesi sözdizimi tarafından etkinleştirilir. Öğe etiketi içinde öznitelik olarak belirtilen özellik yerine, özelliği bir açılış öğesi kullanılarak belirtildiğinde, etiket *elementTypeName*. *propertyName* form, özelliğin değerini içinde belirtilen ve özellik öğesi kapatılır.  
  
 Özellikle, söz dizimi Sol açılı ayraç ile başlar (\<), ardından hemen sınıf veya özellik öğesi sözdizimini kapsamında yer alan yapı türü adı. Bu hemen tek bir nokta (.), ardından bir özellik adıyla sonra sağ açılı ayraç (>) tarafından izlenir. Öznitelik sözdizimiyle gibi bu özellik belirtilen tür genel bildirilen üyeler içinde bulunmalıdır. Özelliğine atanan değer özelliği öğe içinde yer alır. Genellikle değeri olarak bir veya daha fazla nesne öğeleri verilir, nesneleri değerleri belirtme senaryosu olduğundan bu özellik öğe sözdizimini adresine yöneliktir. Son olarak, aynı belirten bir eşdeğer kapanış etiketi *elementTypeName*. *propertyName* birleşimi girilmesi gerekir, uygun iç içe geçme ve diğer öğesi etiketlerle bakiye.  
  
 Örneğin, aşağıdaki özellik öğesi sözdizimi şöyledir <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Değer bir özellik öğesi içinde de iç metin olarak belirtilen özellik türü bir basit değer türü olduğu durumlarda gibi verilebilir <xref:System.String>, veya bir ad belirtilen burada numaralandırması. Bu iki kullanımları biraz seyrek olduklarından bu durumlardan her biri de daha basit bir öznitelik sözdizimini kullanabilirsiniz. XAML içerik özelliği değildir ancak hala UI metin gösterimi için kullanılan özellikler için özellik öğesi bir dizeyle doldurmak için bir senaryo değil ve satır beslemeleri gibi belirli boşluk öğeleri bu UI metin olarak görünmesi gerekir. Öznitelik sözdizimi satır beslemeleri korumak olamaz, ancak önemli boşluk koruma etkin olduğu sürece özellik öğesi sözdizimini kullanabilirsiniz (Ayrıntılar için bkz [XAML'de boşluk işleme](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)). Başka bir senaryo için [x: Uid yönergesi](../../../../docs/framework/xaml-services/x-uid-directive.md) özellik öğesi uygulanabilir ve böylece içindeki değer WPF'de yerelleştirilmiş bir değer BAML çıktı olarak veya başka teknikler işaretleyin.  
  
 Özellik öğesi WPF mantıksal ağaçta temsil edilmez. Özellik öğesi bir özellik ayarlama için yalnızca belirli bir sözdizimi ve bir örnek veya nesneyi, yedekleme sahip bir öğe değil. (Mantıksal ağacının kavram hakkında daha fazla bilgi için bkz: [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).)  
  
 Boşluk işleme gibi subtleties sözdizimleri arasında biraz farklılık gösterir ancak özniteliği ve özellik öğesi sözdizimi desteklendiği özellikleri için iki sözdizimi aynı sonucu genellikle sahiptir.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Koleksiyon sözdizimi  
 XAML belirtimi değer türüne bir koleksiyon olduğu özelliklerini tanımlamak için XAML işlemcisi uygulamaları gerektirir. .NET genel XAML işlemci uygulamasında yönetilen kod ve CLR temel alır ve koleksiyon türleri aşağıdakilerden biri aracılığıyla tanımlar:  
  
-   Implements yazın <xref:System.Collections.IList>.  
  
-   Implements yazın <xref:System.Collections.IDictionary>.  
  
-   Türü türetilen <xref:System.Array> (XAML dizilerde hakkında daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
 Bir özellik türü bir koleksiyon ise, ardından oluşturulursa koleksiyon türü biçimlendirme object öğesi olarak belirtilmesi gerekmez. Bunun yerine, koleksiyondaki öğelerin olmaya yönelik öğeleri bir veya daha çok öğenin alt öğelerini özelliği belirtilir. Her bir öğeyi yüklemesi sırasında bir nesneye değerlendirilir ve çağırarak koleksiyonuna eklenen `Add` zımni koleksiyonunun yöntemi. Örneğin, <xref:System.Windows.Style.Triggers%2A> özelliği <xref:System.Windows.Style> özel koleksiyon türünü alır <xref:System.Windows.TriggerCollection>, hangi uygulayan <xref:System.Collections.IList>. Örneği oluşturmak gerekli değildir bir <xref:System.Windows.TriggerCollection> biçimlendirmede object öğesi. Bunun yerine, bir veya daha fazla belirtin <xref:System.Windows.Trigger> öğeleri içindeki öğeler olarak `Style.Triggers` özellik öğesi, burada <xref:System.Windows.Trigger> (veya türetilmiş bir sınıf) kesin türü belirtilmiş ve örtük öğe türü beklenen tür <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Bu konunun sonraki bölümde ele alınmıştır bir özelliği bir koleksiyon türü ve bu tür için XAML içerik özelliği olabilir ve türetilmiş tür.  
  
 Bir öğe olarak biçimlendirmede görünmez olsa bile bir örtük koleksiyon öğesi üyesi mantıksal ağacının gösterimini oluşturur. Üst tür Oluşturucu örneklemesi özelliklerinden biri koleksiyonu için genellikle gerçekleştirir ve başlangıçta boş bir koleksiyon nesne ağacının bir parçası haline gelir.  
  
> [!NOTE]
>  Genel listesi ve sözlük arabirimler (<xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602>) koleksiyon algılama için desteklenmez. Bununla birlikte, kullanabilirsiniz <xref:System.Collections.Generic.List%601> bunu uyguladığı için bir temel sınıf olarak sınıf <xref:System.Collections.IList> doğrudan veya <xref:System.Collections.Generic.Dictionary%602> bir temel sınıf olarak bunu uyguladığından <xref:System.Collections.IDictionary> doğrudan.  
  
 Koleksiyon türleri için .NET başvurusu sayfalarında, bir koleksiyon için nesne öğesinin kasıtlı atlandığını bu sözdizimiyle bazen XAML sözdizimi bölümlerinde örtük koleksiyonu söz dizimine Not edilir.  
  
 Kök öğe hariç olmak üzere, her nesne başka bir öğenin alt öğesi olarak iç içe bir XAML dosyasındaki öğedir gerçekten birini veya her ikisini aşağıdaki durumlarda olan bir öğeyi: örtük koleksiyon özelliği, üst öğesinin üyesi , veya öğenin üst öğesi (XAML özelliklerini ilerideki bölümde açıklanır içerik) için XAML İçerik özelliğinin değeri belirtir. Diğer bir deyişle, ilişki üst öğeleri ve bir işaretleme sayfasında alt öğeleri gerçekten kökünde tek bir nesne, ve her nesne kökü altındaki bir özellik değeri üst sağlayan tek bir örnek ya da bir sütun içindeki öğelerden birini öğedir Ayrıca bir koleksiyon türü özelliği üst değerdir seçimi. Bu tek köklü kavramı XML ile yaygındır ve XAML gibi yük API'leri davranışındaki sık güçlendirilmiş <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Aşağıdaki örnek bir koleksiyon için nesne öğesi olan bir sözdizimi şöyledir (<xref:System.Windows.Media.GradientStopCollection>) açıkça belirtilen.  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 Bu her zaman açıkça topluluğun bildirin mümkün olmadığını unutmayın. Örneğin, bildirme girişiminde <xref:System.Windows.TriggerCollection> açıkça içinde daha önce gösterilen <xref:System.Windows.Style.Triggers%2A> örnek başarısız olurdu. Koleksiyon açıkça bildirme gerektirir koleksiyon sınıfı varsayılan bir oluşturucu desteklemesi gerekir ve <xref:System.Windows.TriggerCollection> varsayılan bir oluşturucu yok.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML İçerik özellikleri  
 XAML içerik sözdizimi yalnızca belirttiğiniz sınıfları üzerinde etkin bir söz dizimi şöyledir <xref:System.Windows.Markup.ContentPropertyAttribute> kendi sınıf bildiriminin bir parçası olarak. <xref:System.Windows.Markup.ContentPropertyAttribute> İçerik özelliği (türetilen sınıflar dahil) öğesi türü için özellik adını başvuruyor. XAML processor tarafından işlenen, bu nesne için XAML İçerik özelliğinin değeri olması için herhangi bir alt öğe veya açılış ve nesne öğenin kapatma etiketi arasına bulunan iç metni atanır. İçerik özelliği için açık özellik öğeleri belirtmek için izin verilen, ancak bu kullanım .NET başvurusu XAML sözdizimi bölümlerinde genellikle gösterilmez. Açık/verbose teknik biçimlendirme anlaşılması için veya sağlasa da, biçimlendirme stili olarak zaman zaman değeri gerekiyor, ancak genellikle içerik özelliği amacı üst-alt sezgisel ilişkili öğeleri doğrudan iç içe böylece işaretleme kolaylaştırmak için. Bir öğe üzerinde diğer özellikler için özellik öğesi etiketleri katı bir XAML dili tanımının; başına "içerik" olarak atanmaz Bunlar XAML ayrıştırıcısı 's işleme sırayla daha önce işlenir ve "içerik" olarak dikkate alınmaz.  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML içeriği özellik değerlerini bitişik olmalıdır  
 XAML İçerik özelliğinin değeri tamamen önce veya tamamen sonra herhangi bir özellik öğe bu nesnenin öğede verilmesi gerekir. XAML içeriği özelliğinin değeri bir dize olarak veya bir veya daha fazla nesne olarak belirtilmiş olsa da olmasa bu durum geçerlidir. Örneğin, aşağıdaki biçimlendirme ayrıştırma değil:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Bu temelde geçersiz içerik özellik için özellik öğesi sözdizimini kullanarak bu söz dizimini açık yapılmışsa sonra içerik özelliği iki kez ayarlanması çünkü:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Benzer şekilde geçersiz bir örnek içerik özelliği bir koleksiyonudur ve alt öğelerini özelliği öğeleriyle interspersed verilmiştir:  
  
```xml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>İçerik özellikleri ve birleştirilmiş toplama sözdizimi  
 Kabul etmek için en fazla bir tek nesne öğesi içeriği, içerik özelliğinin türü özellikle koleksiyon türü olmalıdır. Özellik öğesi sözdizimini koleksiyon türleri için benzer bir XAML işlemci koleksiyon türleri olan türlerini tanımlamanız gerekir. XAML içerik özelliği bir öğeye sahip olan ve XAML içerik özelliği bir koleksiyon türüdür durumunda zımni koleksiyon türü bir nesne öğesi olarak işaretleme belirtilmesi gerekmez ve XAML içerik özelliği bir özellik el belirtilmesi gerekmez. Yönetim. Bu nedenle işaretleme görünen içerik modelinde artık içeriği olarak atanmış birden fazla alt öğe olabilir. Aşağıdaki içerik için söz dizimi bir <xref:System.Windows.Controls.Panel> türetilmiş sınıf. Tüm <xref:System.Windows.Controls.Panel> türetilen sınıflar kurmak XAML içerik özelliğini <xref:System.Windows.Controls.Panel.Children%2A>, türünde bir değer gerektiren <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Unutmayın hiçbiri özellik öğesi için <xref:System.Windows.Controls.Panel.Children%2A> veya öğe için <xref:System.Windows.Controls.UIElementCollection> biçimlendirmede gereklidir. Böylece yinelemeli olarak tanımlayan öğeleri bulunan bu tasarım XAML özelliğidir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ağacı müdahalede bulunan özellik öğesi etiketleri olmadan hemen üst-alt öğe ilişkileri olan iç içe geçmiş öğe olarak gösterilen daha sezgisel olan veya koleksiyon nesnesi. Aslında, <xref:System.Windows.Controls.UIElementCollection> tasarım gereği açıkça biçimlendirmede bir nesne öğesi olarak belirtilemez. Yalnızca kullanıma örtük bir koleksiyonu olduğundan <xref:System.Windows.Controls.UIElementCollection> ortak varsayılan bir oluşturucu kullanıma sunmuyor ve bu nedenle bir nesneyi öğesi olarak başlatılamaz.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Özellik öğelerini ve içerik bir özelliği olan bir nesne, nesne öğelerini karıştırma  
 XAML belirtimi XAML işlemci XAML içerik özelliği bir nesne öğesi içinde doldurmak için kullanılan nesne öğeleri bitişik olmalı ve değil karışık olmalı zorunlu kılabilir bildirir. Bu kısıtlama özellik öğelerini ve içerik karıştırma karşı tarafından zorlanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemcileri.  
  
 Bir nesne öğesi içinde ilk hemen biçimlendirmesi olarak bir alt nesne öğesi olabilir. Ardından özellik öğelerinin ortaya çıkarabilir. Veya, bir veya daha fazla özellik öğeleri, sonra içerik sonra daha fazla özellik öğelerinin belirtebilirsiniz. Ancak bu özellik öğesi içeriği izleyen sonra herhangi bir içerik yapamazsınız, yalnızca özellik öğeleri ekleyebilirsiniz.  
  
 Bu içerik / özellik öğesi sipariş gereksinim içeriği olarak kullanılan iç metni için geçerli değildir. Ancak, önemli boşluk özellik öğelerinin iç metinle interspersed biçimlendirmede görsel olarak saptamak zor olduğundan iç metni bitişik, tutmak için iyi biçimlendirme stili hala vardır.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML Ad Uzayları  
 Önceki sözdizimi örneklerini hiçbiri varsayılan XAML ad uzayı dışında XAML ad uzayı belirtilmiş. Tipik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları, XAML ad uzayı varsayılan olarak belirtilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ad alanı. XAML ad uzayları varsayılan XAML ad uzayı dışında belirtin ve hala benzer sözdizimini kullanın. Ancak daha sonra herhangi bir yere bir sınıf, varsayılan XAML ad uzayı içinde erişilebilir durumda değil burada adlı bu sınıf adı XAML ad alanı öneki ile ilgili CLR ad alanına eşlenmiş olarak gelmelidir. Örneğin, `<custom:Example/>` bir örneği için nesne öğesi sözdizimini `Example` burada o sınıfın (ve muhtemelen yedekleme türleri içeren dış derleme bilgilerini) içeren CLR ad alanı önceden eşlenmiş sınıfı `custom` öneki.  
  
 XAML ad uzayları hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML Namespace eşleme](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>İşaretleme uzantıları  
 XAML biçimlendirme uzantısı normal XAML işlemci işlenmesini dize öznitelik değerleri ya da nesne öğeleri'den bir çıkış sağlar ve işleme bir yedekleme sınıfına kadar erteler varlık programlama tanımlar. XAML işlemciye biçimlendirme uzantısı öznitelik sözdizimini kullanarak bir kapanış kaşlı ayraç (}) dışında herhangi bir karakter arkasından parantezinden ({}) olduğunda tanımlayan karakter. Bu alt dizeyi doğru sınıf adı bir parçası ise "Uzantısı" başvuru alt dizeyi burada atlayın belirli uzantısı davranışı sağlayan sınıf parantezinden aşağıdaki ilk dizesi başvurmalıdır. Bundan sonra tek bir boşluk görünebilir ve kapanış kuşak karşılaştı kadar sonra izleyen her karakter giriş olarak uzantısı uygulaması tarafından kullanılır.  
  
 .NET XAML uygulama kullanan <xref:System.Windows.Markup.MarkupExtension> tüm tarafından desteklenen biçimlendirme uzantıları için temel olarak soyut sınıf [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diğer çerçeveler veya teknolojileri yanı sıra. Biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikle uygulayan diğer varolan nesneleri başvuru ya da çalışma zamanında değerlendirilir nesnelere ertelenmiş başvuru yapmak için bir yol sağlamak için çoğunlukla yöneliktir. Örneğin, bir Basit WPF veri bağlama belirterek gerçekleştirilir `{Binding}` biçimlendirme uzantısı yerine belirli bir özellik normalde götürecek değeri. WPF biçimlendirme uzantıları birçoğu, burada bir öznitelik sözdizimi aksi mümkün olmayacaktır özellikleri için bir öznitelik sözdizimi etkinleştirin. Örneğin, bir <xref:System.Windows.Style> iç içe geçmiş dizi nesneleri ve özellikleri içeren bir oldukça karmaşık türü bir nesnedir. WPF stillerde bir kaynak olarak tanımlanmış genellikle bir <xref:System.Windows.ResourceDictionary>ve bir kaynak isteği iki WPF biçimlendirme uzantıları biri aracılığıyla başvurulabilir. İşaretleme uzantısı kaynak arama özellik değerine değerlendirmesi erteler ve değeri sağlama sağlar <xref:System.Windows.FrameworkElement.Style%2A> türü alma özelliği, <xref:System.Windows.Style>, öznitelik sözdizimi aşağıdaki örnekteki gibi:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Burada, `StaticResource` tanımlayan <xref:System.Windows.StaticResourceExtension> biçimlendirme uzantısı uygulama sağlayan sınıf. Sonraki dize `MyStyle` giriş olarak varsayılan olmayan için kullanılan <xref:System.Windows.StaticResourceExtension> burada uzantı dizeden gerçekleştirilecek şekilde parametrenin bildirir istenen Oluşturucusu <xref:System.Windows.ResourceKey>. `MyStyle`olması bekleniyor [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) değerini bir <xref:System.Windows.Style> bir kaynak olarak tanımlanmış. [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) kullanım istekleri kaynak sağlamak için kullanılan <xref:System.Windows.Style> statik kaynak arama mantığını yükleme zamanında aracılığıyla özellik değeri.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md). Biçimlendirme uzantıları ve özellikleri genel .NET XAML uygulamasında etkin programlama diğer XAML başvuru için bkz: [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). WPF özgü biçimlendirme uzantıları için bkz: [WPF XAML uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Ekli Özellikler  
 Ekli özellikler yapabildiği özellikler ait ve belirli bir tür tarafından tanımlanan XAML'de sunulan bir programlama kavramı olan herhangi bir öğe üzerinde öznitelikleri veya özellik öğeleri olarak ancak ayarlayın. Birincil senaryo ekli özellikler için tasarlanmıştır alt öğelerini bir üst öğeye rapor bilgilere biçimlendirme yapısındaki tüm öğeler arasında yaygın paylaşılan nesne modeli gerektirmeden sağlamaktır. Buna karşılık, ekli özellikler, alt öğeler için rapor bilgilere üst öğeler tarafından kullanılabilir. Ekli özellikler ekli özellikler ve kendi oluşturma amacı hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Ekli özellikler kullanmak yüzeysel olarak özellik öğesi sözdizimi, benzer bir sözdizimi da belirttiğiniz bir *typeName*. *propertyName* birleşimi. İki önemli farklılıklar vardır:  
  
-   Kullanabileceğiniz *typeName*. *propertyName* öznitelik sözdizimi ile iliştirilmiş özellik ayarlarken bile birleşimi. Yalnızca özellik adı uygun yerlerde bir gereksinim bir öznitelik sözdiziminde durumdur ekli özelliklerdir.  
  
-   Ekli özellikler için özellik öğesi sözdizimini de kullanabilirsiniz. Ancak, tipik özellik öğesi sözdizimi için *typeName* belirttiğiniz öğesidir özellik öğesi içeren nesne. Ekli bir özellik için başvuruyorsanız sonra *typeName* değil içeren object öğesi iliştirilmiş özelliği tanımlayan bir sınıftır.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Ekli Olaylar  
 Ekli olaylar burada olayları belirli bir türüyle tanımlanabilir, ancak herhangi bir nesne öğede işleyicilerinin XAML'de sunulan başka bir programlama kavramıdır. WOF uygulamasında genellikle ekli olay tanımlayan türü bir hizmet tanımlayan bir statik türdür ve hizmeti kullanıma türleri yönlendirilmiş olay diğer adı tarafından ekli olaylar bazen gösteriliyor demektir. Ekli olaylar için işleyiciler öznitelik sözdizimi ile belirtilir. Ekli olaylar ile öznitelik sözdizimi ekli olaylar izin vermek genişletilir gibi bir *typeName*. *eventName* kullanımı, burada *typeName* sağlayan sınıfının `Add` ve `Remove` ekli olay altyapısı için olay işleyicisini erişimcileri ve *eventName* olay adı.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML kök öğesi anatomisi  
 Aşağıdaki tabloda, belirli bir kök öğesi özniteliklerini gösteren böldük, tipik bir XAML kök öğesi gösterilmektedir:  
  
|||  
|-|-|  
|`<Page`|Object öğesi kök öğesinin açma|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Varsayılan değer ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML ad uzayı|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML dili XAML ad uzayı|  
|`x:Class="ExampleNamespace.ExampleCode"`|İşaretleme için kod arka plan herhangi bağlanır parçalı sınıf bildirimi kısmi sınıfı için tanımlanmış|  
|`>`|Object öğesi kök sonu. Öğenin alt öğeler içerdiğinden nesne henüz kapalı|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>İsteğe bağlı ve Nonrecommended XAML kullanımları  
 Teknik olarak XAML işlemcileri tarafından desteklenen, ancak ayrıntı veya ne zaman okunabilir kalan XAML dosyalarıyla müdahale diğer estetik sorunları üretmek XAML kullanımları aşağıdaki bölümlerde, XAML kaynakları içeren uygulamalar geliştirin .  
  
### <a name="optional-property-element-usages"></a>İsteğe bağlı özellik öğesi kullanımları  
 İsteğe bağlı özellik öğesi kullanımları XAML işlemci örtük olarak değerlendirir, öğe içerik özellikleri açıkça yazma içerir. Örneğin, ne zaman bildirdiğiniz içeriğini bir <xref:System.Windows.Controls.Menu>, açıkça bildirmek seçebilir <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu <xref:System.Windows.Controls.Menu> olarak bir `<Menu.Items>` özellik öğesi etiketi ve yer her <xref:System.Windows.Controls.MenuItem> içinde `<Menu.Items>`, bunun yerine örtük XAML işlemci davranışı kullanmaktan, tüm alt öğeleri bir <xref:System.Windows.Controls.Menu> olmalıdır bir <xref:System.Windows.Controls.MenuItem> ve yerleştirilir <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu. Bazen isteğe bağlı kullanımları biçimlendirmede temsil edilen nesne yapısını görsel olarak açıklamak için yardımcı olabilir. Veya bir açık özellik öğesi kullanımı görsel olarak, bir öznitelik değeri içinde iç içe geçmiş biçimlendirme uzantıları gibi kafa karıştırıcı ancak teknik olarak işlev biçimlendirme bazen önleyebilirsiniz.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Tam tam typeName.memberName öznitelikleri  
 *TypeName*. *memberName* bir öznitelik gerçekte yalnızca yönlendirilmiş olay çalışması daha Evrensel çalıştığı için form. Ancak diğer durumlarda, form gereksiz ve yalnızca nedenlerinden biçimlendirme stili ve okunabilirliği varsa, kaçınmalısınız. Aşağıdaki örnekte, her üç başvurular <xref:System.Windows.Controls.Control.Background%2A> özniteliği tamamen eşdeğerdir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`çalışır çünkü bu özellik için tam arama <xref:System.Windows.Controls.Button> başarılı (<xref:System.Windows.Controls.Control.Background%2A> denetiminden devralındı) ve <xref:System.Windows.Controls.Button> object öğesi sınıf ya da bir taban sınıfı. `Control.Background`çalışır çünkü <xref:System.Windows.Controls.Control> sınıfı gerçekten tanımlayan <xref:System.Windows.Controls.Control.Background%2A> ve <xref:System.Windows.Controls.Control> olan bir <xref:System.Windows.Controls.Button> temel sınıfı.  
  
 Ancak, aşağıdaki *typeName*. *memberName* form örneği çalışmaz ve bu nedenle açıklamalı gösterilir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>başka bir türetilmiş sınıf <xref:System.Windows.Controls.Control>, ve belirtilmişse `Label.Background` içinde bir <xref:System.Windows.Controls.Label> object öğesi, bu kullanım çalışılan. Ancak, çünkü <xref:System.Windows.Controls.Label> sınıfı veya temel sınıfını değil <xref:System.Windows.Controls.Button>, belirtilen XAML işlemci sonra işlemek üzere davranıştır `Label.Background` eklenen bir özellik olarak. `Label.Background`kullanılabilir iliştirilmiş bir özellik değildir ve bu kullanım başarısız olur.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName özelliği öğeleri  
 Benzer bir şekilde nasıl *typeName*. *memberName* form çalışır öznitelik sözdizimi için bir *baseTypeName*. *memberName* sözdizimi özellik öğesi sözdizimi için çalışır. Örneğin, aşağıdaki söz dizimini çalışır:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Özellik öğesi olarak burada verilen `Control.Background` özellik öğesi içinde yer alan olsa bile `Button`.  
  
 Ancak olduğu gibi *typeName*. *memberName* öznitelikleri için form *baseTypeName*. *memberName* biçimlendirmede zayıf stili ve kaçınmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XAML Ad Alanı (x:) Dil Özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML Uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
