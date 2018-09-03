---
title: Ayrıntılı XAML Sözdizimi
ms.date: 03/30/2017
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
ms.openlocfilehash: eabb9c84824a4604319a346612e84563abaf2b76
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485735"
---
# <a name="xaml-syntax-in-detail"></a>Ayrıntılı XAML Sözdizimi
Bu konuda, XAML söz dizimi öğeleri tanımlamak için kullanılan terimleri tanımlar. Bu terimler sık kalanında bu belge, WPF belgeler için her ikisi de özellikle ve XAML veya XAML dil desteğini System.Xaml düzeyinde Etkin temel XAML kavramları kullanan diğer çerçeveler için kullanılır. Bu konu başlığı altında bu konu başlığı altında tanıtılan temel terminoloji genişletir. [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML dil belirtimi  
 Burada tanımlanan XAML sözdizimi terminolojisi ayrıca tanımlanan veya başvurulan içinde XAML dil belirtimi. XAML aşağıdaki XML tabanlı bir dildir ve XML yapısal kuralları üzerinde genişletir. Bazı terimler, paylaşılan veya XML dil veya XML belge nesne modeli anlatırken yaygın olarak kullanılan terimler hakkında temel alır.  
  
 XAML dil belirtimi hakkında daha fazla bilgi için indirme [ \[MS-XAML\] ](https://go.microsoft.com/fwlink/?LinkId=114525) Microsoft Download Center öğesinden.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML ve CLR  
 XAML biçimlendirme dilidir. [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], Etkinleştirir çalışma zamanı yürütme adını kullanarak örtük olarak. XAML kendisi tarafından doğrudan CLR çalışma zamanı tarafından kullanılan ortak dillerden biri değil. Bunun yerine XAML, kendi tür sistemi destek olarak düşünebilirsiniz. WPF tarafından kullanılan belirli XAML ayrıştırma system CLR ve CLR tür sistemi üzerinde oluşturulmuştur. XAML türlerini çalışma zamanında gösterimi WPF için XAML ayrıştırıldığında örneklemek için CLR türlerine eşlenir. XAML dil belirtimi eşdeğer söz tartışmalarına gerekmese bile bu nedenle, CLR tür sistemi başvuruları geri kalanında bu belgede söz dizimi hakkında ayrıntılı bilgi içerir. (XAML dil belirtimi düzeyi başına XAML türleri, CLR olması gerekmez, ancak oluşturulmasını ve farklı bir XAML ayrıştırıcı kullanımını gerektirecek herhangi diğer tür sistemine eşleştirilebilir.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Üyeleri türlerine ve sınıf devralma  
 Özellikleri ve olayları olarak XAML üyesi olarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türü genellikle temel türlerden devralınan. Örneğin, bu örneği göz önünde bulundurun: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> Özelliği değil hemen bildirilen bir özellik üzerinde <xref:System.Windows.Controls.Button> sınıf tanımı, yansıma sonuçları veya belgelere bakmak için olsaydı, sınıf. Bunun yerine, <xref:System.Windows.Controls.Control.Background%2A> temelden devralınan <xref:System.Windows.Controls.Control> sınıfı.  
  
 Sınıf devralma davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML öğeleri olan bir şema tarafından zorlanan yorumu XML Biçimlendirme gelen önemli ölçüde farklıdır. Sınıf devralma özellikle Ara temel sınıflarının soyut veya arabirim söz konusu olduğunda karmaşık hale gelebilir. Tipik olarak kullanılan XAML öğeleri ve izin verilen öznitelikleri kümesini doğru bir şekilde ve tam şema türü kullanarak temsil etmek zor olan bir nedeni budur [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , DTD'nin veya XSD biçiminde gibi programlama. Başka bir nedeni, genişletilebilirlik ve bütünlük tüm sabit temsilinin izin verilen türler ve üyeler tür eşlemesi XAML dil özelliklerinin kullanımını.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Nesne öğesi sözdizimi  
 *Nesne öğesi sözdizimi* bir XML öğesi bildirerek bir CLR sınıf veya yapı başlatan XAML biçimlendirme sözdizimi aşağıdaki gibidir. Bu sözdizimi, diğer biçimlendirme diller gibi HTML öğesi sözdizimi benzer. Nesne öğesi sözdizimi bir sol açılı ayraç ile başlar (\<), ardından sınıf veya yapının örneği oluşturulan tür adı. Sıfır veya daha fazla boşluk tür adı izleyebilir ve sıfır veya daha fazla öznitelik de bildirilen nesne öğesi her bir öznitelik adı ayıran bir veya daha fazla boşluk ile "value" eşleştirmesi. Son olarak, aşağıdakilerden biri doğru olmalıdır:  
  
-   Öğesini ve etiket bir sağ açılı ayraç (>) hemen ardından bir eğik çizgi (/) tarafından kapatılmalıdır.  
  
-   Açılış etiketinde bir sağ açılı ayraç (>) tamamlanması gerekir. Diğer nesne öğeleri, özellik öğelerinin veya iç metin, açılış etiketinde takip edebilirsiniz. Tam olarak hangi içeriği burada bulunabilecek genellikle öğesi nesne modeli tarafından sınırlanır. Kapanış etiketi nesne öğesi eşdeğer Ayrıca, uygun iç içe geçme mevcut ve diğer açılış ve kapanış etiketi çiftleri ile dengelemeniz gerekir.  
  
 .NET tarafından uygulandığı gibi XAML nesne öğelerinin türleri, özellikleri veya olayları ve CLR ad alanları ve bütünleştirilmiş kod için XAML ad alanları öznitelikler içine eşleyen kuralları kümesi vardır. WPF ve .NET Framework için XAML nesne öğelerini eşleyin [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] başvurulan derlemeler içinde tanımlanan türleri ve öznitelikleri eşlemek için bu türlerin üyeleri. Bir CLR türü XAML içinde başvurduğunuzda, devralınan üyeleri de o türdeki erişiminiz vardır.  
  
 Örneğin, aşağıdaki örnek yeni bir örneğini başlatan nesne öğesi sözdizimi, <xref:System.Windows.Controls.Button> sınıfı ve ayrıca belirten bir <xref:System.Windows.FrameworkElement.Name%2A> özniteliği ve bu öznitelik için bir değer:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Aşağıdaki örnekte, XAML içerik özelliği söz dizimi de içeren bir nesne öğesi sözdizimi bulunur. İçindeki iç metni ayarlamak için kullanılan <xref:System.Windows.Controls.TextBox> XAML içerik özelliği, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>İçerik modelleri  
 Bir sınıf bir kullanım söz dizimi bakımından XAML nesne öğesi olarak desteklemiyor olabilir, ancak bir genel içerik modeli veya öğesi ağacı beklenen konumda yerleştirildiğinde bu öğe yalnızca bir uygulama veya sayfa düzgün çalışır. Örneğin, bir <xref:System.Windows.Controls.MenuItem> genellikle yalnızca bir alt öğesi olarak yerleştirilmesi gereken bir <xref:System.Windows.Controls.Primitives.MenuBase> gibi türetilmiş sınıf <xref:System.Windows.Controls.Menu>. İçerik modelleri belirli öğeler için sınıf sayfalarında ve diğer denetimler için açıklamalar bir parçası olarak belgelenmiştir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML öğeleri olarak kullanılabilir sınıflar.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Nesne öğelerin özellikleri  
 XAML özelliklerinde olası sözdizimleri çeşitli tarafından ayarlanır. Hangi sözdizimi, belirli bir özellik için kullanılabilir, ayarladığınız bir özelliğin temel alınan türü sistem özelliklerine göre değişir.  
  
 Çalışma süresi nesne grafiğinde oldukları gibi özelliklerin değerlerini ayarlayarak, özellikler veya özellikleri nesneleri eklersiniz. Bir nesne öğesinden oluşturulan nesnenin ilk durumu varsayılan oluşturucu davranış temel alır. Genellikle, uygulamanızı tamamen varsayılan örneği herhangi bir nesne dışında bir şey kullanırsınız.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (Özellikler)  
 Öznitelik, bir özellik için bir değer var olan bir nesne öğesi üzerinde bir öznitelik bildirerek ayarlar XAML biçimlendirme sözdizimi sözdizimidir. Öznitelik adı, ilgili nesne öğesi yedekler sınıf özelliğin CLR üye adı eşleşmelidir. Öznitelik adı bir atama işleci (=) izler. Öznitelik değeri tırnak alınmış bir dize olmalıdır.  
  
> [!NOTE]
>  Bir öznitelik içinde bir değişmez değer tırnak işareti yerleştirmek için Alternatif teklifler kullanabilirsiniz. Örneği için bir yol tek tırnak içindeki bir çift tırnak karakteri içeren bir dize bildirmek için kullanabilirsiniz. Tek veya çift tırnak işareti kullanın, açma ve öznitelik değeri dize kapatma için eşleşen bir çift kullanmalısınız. Ayrıca vardır kaçış dizileri veya diğer teknikleri belirli XAML söz dizimi karakter kısıtlamalarınız etrafında çalışma için kullanılabilir. Bkz: [XML karakter varlıkları ve XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 Öznitelik söz dizimi aracılığıyla ayarlamak için bir özellik genel olmalıdır ve yazılabilir olması gerekir. Örneği veya ilgili erişirken bir XAML işlemcisi tarafından başvurulan bir başvuru türü, tür yedekleme gerekir veya yedekleme tür sisteminde özelliğinin değeri bir değer türü olmalıdır.  
  
 WPF XAML olaylar için öznitelik adı başvurulan bir olay genel ve genel temsilci olması gerekir.  
  
 Özellik veya olay, bir sınıf ya da içeren bir nesne öğesi tarafından oluşturulan yapı üyesi olması gerekir.  
  
### <a name="processing-of-attribute-values"></a>Öznitelik değerleri işleme  
 Açılış ve kapanış tırnak işareti içinde yer alan dize değeri bir XAML işlemcisi tarafından işlenir. Özellikler için varsayılan davranış işleme temel alınan CLR özelliğinin türü tarafından belirlenir.  
  
 Öznitelik değeri aşağıdakilerden biri tarafından doldurulur bu işlem sırasını kullanarak:  
  
1.  XAML işlemci küme ayracı ve türeyen bir nesne öğesi karşılaşırsa <xref:System.Windows.Markup.MarkupExtension>ardından değeri bir dize olarak işleme yerine ilk başvurulan işaretleme uzantısı değerlendirilir ve İşaretleme uzantısı tarafından döndürülen nesne olarak kullanılır değer. Çoğu durumda, bir işaretleme uzantısı tarafından döndürülen nesne var olan bir nesne veya değerlendirme çalıştırma kadar erteler ve yeni oluşturulmuş bir nesne değil bir ifade başvuru olacaktır.  
  
2.  Özellik bildirilirse bir öznitelik ile <xref:System.ComponentModel.TypeConverter>, veya bu özellik değer türünde bildirilen bir öznitelik ile <xref:System.ComponentModel.TypeConverter>özniteliğinin dize değerini tür dönüştürücüsünü bir dönüştürme giriş olarak gönderilir ve dönüştürücü döndüreceği bir Yeni nesne örneği.  
  
3.  Yoksa hiçbir <xref:System.ComponentModel.TypeConverter>, özellik türü doğrudan dönüştürmeyi denedi. Bu son düzeyi, XAML dili temel türlerin veya adlandırılmış sabitler (ardından ayrıştırıcının eşleşen değerleri na erişir) bir numaralandırmada Adları Denetle arasında ayrıştırıcı yerel değerde doğrudan bir dönüştürmedir.  
  
#### <a name="enumeration-attribute-values"></a>Sabit listesi öznitelik değerleri  
 XAML numaralandırmalardan doğası gereği XAML ayrıştırıcıları tarafından işlenir ve sabit listesinin adlandırılmış sabitler, dize adını belirterek bir sabit listesi üyesi belirtilmelidir.  
  
 Nonflag numaralandırma değerleri için yerel bir öznitelik değeri dize işleme ve numaralandırma değerlerinden biri olarak çözmek için bir davranıştır. Numaralandırma biçimi belirtmeyin *numaralandırma*. *Değer*, kodda yaptığınız gibi. Bunun yerine, yalnızca belirttiğiniz *değer*, ve *numaralandırma* ayarladığınızdan özelliğinin türü tarafından algılanır. Bir özniteliği belirtirseniz *numaralandırma*. *Değer* formu, çözümlenmeyen doğru.  
  
 Davranış dayanır flagwise sabit listeleri için <xref:System.Enum.Parse%2A?displayProperty=nameWithType> yöntemi. Her değeri virgülle ayırarak flagwise numaralandırması için birden çok değer belirtebilirsiniz. Ancak, flagwise olmayan sabit listesi değerleri birleştiremezsiniz. Oluşturma girişiminde bulunmak virgülle sözdizimi örneği için kullanamazsınız bir <xref:System.Windows.Trigger> nonflag sabit listesi birden çok koşulu temel görevi görür:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 WPF'de XAML içinde ayarlanabilir öznitelikleri destekleyen flagwise numaralandırmalar nadirdir. Ancak, bu tür bir numaralandırma olan <xref:System.Windows.Media.StyleSimulations>. Örneği için virgülle ayrılmış flagwise öznitelik sözdizimi açıklamaları için sağlanan örnek değiştirmek için kullanabilirsiniz <xref:System.Windows.Documents.Glyphs> sınıf; `StyleSimulations = "BoldSimulation"` olabileceği `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> Burada birden fazla numaralandırma değeri belirtilebilir başka bir özelliktir. Ancak, bu özellik bir özel durum nedeniyle özelleştirmede <xref:System.Windows.Input.ModifierKeys> numaralandırma kendi tür dönüştürücüsü destekler. Değiştiriciler için tür dönüştürücüsünü bir ayırıcı virgül (,) yerine bir artı işareti (+) kullanır. Bu dönüştürme "Ctrl + Alt" gibi Microsoft Windows programlamada, tuş birleşimleri göstermek için daha geleneksel sözdizimini destekler.  
  
### <a name="properties-and-event-member-name-references"></a>Özellikler ve olay üye adı başvuruları  
 Bir öznitelik belirtirken, herhangi bir özelliği veya CLR türü içeren bir nesne öğesi için örneği bir üyesi olarak var olan olay başvurabilirsiniz.  
  
 Veya ekli özelliği başvurabilir veya ekli olay içeren nesne öğesi bağımsız. (İliştirilmiş özellikler gelecek bölümde ele alınmıştır.)  
  
 Kullanarak varsayılan ad alanı erişilebilen herhangi bir nesneden herhangi bir olay adının da bir *typeName*. *olay* kısmen nitelenmiş ad; yönlendirilmiş olaylar için işleyiciler eklenmesini destekler işleyici burada alt öğeleri, ancak üst öğe yönlendirme olayları işlemek için tasarlanmıştır sahip değil aynı zamanda olay üyeler tablosunda bu söz dizimi. Bu söz dizimi ekli olay sözdizimi benzer, ancak burada olayı true ekli bir olay değil. Bunun yerine, bir tam adı ile bir olay başvuruda bulunuyor. Daha fazla bilgi için [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Bazı senaryolarda, özellik adları, öznitelik adı yerine bir öznitelik değeri olarak bazen sağlanır. Bu özellik adı biçiminde belirtilen özellik gibi bir niteleyici de içerebilir *ownerType*. *dependencyPropertyName*. Bu senaryo, stilleri veya şablonları XAML yazarken yaygındır. Özellik adlarının bir öznitelik değeri sağlanan işleme kurallarına farklıdır ve ayarlanan özelliğin türünü veya belirli WPF alt sistemlerin davranış tarafından yönetilir. Ayrıntılar için bkz [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Bir öznitelik değeri bir özellik özelliği ilişki açıkladığında özellik adları için başka bir kullanımdır. Bu özellik, veri bağlama ve görsel taslak hedefler için kullanılır ve etkinleştirilir <xref:System.Windows.PropertyPath> sınıf ve onun tür dönüştürücü. Arama semantikleri daha eksiksiz bir açıklaması için bkz. [PropertyPath XAML söz dizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Özellik öğesi sözdizimi  
 *Özellik öğesi sözdizimine* öğeleri için temel XML sözdizimi kurallarına davranışından kareninkinden sözdizimidir. XML, pratikte bir dize bir öznitelik değeri, yalnızca değişim ile hangi dize kodlama biçimi kullanılmakta olan. XAML içinde bir özellik değeri olması için diğer nesne öğeleri atayabilirsiniz. Bu özellik, özellik öğesi sözdizimi tarafından etkinleştirilir. Öznitelik öğesi etiketi içinde olarak belirtilen özellik yerine özelliği açılış öğesini kullanarak belirtilen içindeki *elementTypeName*. *propertyName* form içinde belirtilen özelliğin değerini ve özellik öğesi kapatılır.  
  
 Özellikle, söz dizimi bir sol açılı ayraç ile başlar (\<), ardından sınıf ya da özellik öğesi sözdizimine içinde yer alan bir yapı türü adı. Bu hemen tek bir nokta (.), ardından bir özellik adıyla sonra bir sağ açılı ayraç (>) takip eder. Öznitelik sözdizimi olarak ile bu özelliği içinde belirtilen türde bildirilen genel üyeleri mevcut olması gerekir. Özelliğe atanacak değer özellik öğesi içinde yer alır. Genellikle değeri olarak bir veya daha fazla nesne öğeleri verilir, nesneleri, değer olarak belirterek senaryo olduğundan bu özellik öğesi sözdizimine adresine yöneliktir. Son olarak, aynı belirten bir eşdeğer kapanış etiketi *elementTypeName*. *propertyName* birlikte sağlanmalıdır, uygun iç içe geçirme ve diğer öğesi etiketleri ile bakiye.  
  
 Örneğin, özellik öğesi sözdizimi aşağıdaki gibidir <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Değer bir özellik öğesi içinde ayrıca iç metin olarak belirtilen özellik türü bir basit değer türü olduğu durumlarda gibi verilebilir <xref:System.String>, veya bir numaralandırma burada bir ad belirtilir. Bu iki kullanımı biraz nadir olduğu her durumda daha basit bir öznitelik söz dizimi de kullanabilirsiniz. XAML içerik özelliği değildir ancak yine de UI metni bir gösterimi için kullanılan özellikler için özellik öğesi ile bir dize doldurmak için bir senaryo olduğundan ve karakterlerine gibi belirli boşluk öğeleri bu UI metni görünmesi gerekir. Öznitelik sözdizimi karakterlerine korumak olamaz, ancak önemli boşluk korunması etkin olduğu sürece özellik öğesi sözdizimini kullanabilirsiniz (Ayrıntılar için bkz [XAML içinde işleme boşluk](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)). Başka bir senaryodur. böylece [x: Uid yönergesi](../../../../docs/framework/xaml-services/x-uid-directive.md) özelliği öğesine uygulanabilir ve bu nedenle içindeki değer WPF'de yerelleştirilmiş bir değer BAML çıktı olarak veya diğer teknikleri işaretleyin.  
  
 Bir özellik öğesi WPF mantıksal ağaçta temsil edilmez. Bir özellik öğesi bir özelliği ayarlamak için yalnızca bir özel sözdizimi ve bir örnek veya yedekleyen nesne sahip bir öğe değil. (Mantıksal ağaç kavramı hakkında daha fazla bilgi için bkz: [WPF içinde ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).)  
  
 Boşluk işleme gibi ıot'nin sözdizimleri arasında biraz farklılık gösterebilir ancak hem öznitelik hem de özellik öğesi sözdizimi desteklendiği özelliklerini, iki sözdizimi aynı sonucu genellikle sahiptir.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Koleksiyon söz dizimi  
 Değer türü bir koleksiyon olduğu özellikleri tanımlamak için XAML işlemcisi uygulamaları XAML belirtimi gerektirir. . NET'te genel XAML işlemci uygulamasında, yönetilen kod ve CLR temel alır ve koleksiyon türleri aşağıdakilerden biri aracılığıyla tanımlar:  
  
-   Uygulayan türü <xref:System.Collections.IList>.  
  
-   Uygulayan türü <xref:System.Collections.IDictionary>.  
  
-   Tür türetilir <xref:System.Array> (XAML içindeki diziler hakkında daha fazla bilgi için bkz: [x: Array işaretleme uzantısı](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
 Özellik türü bir koleksiyon, ardından çıkarsanan koleksiyon türü bir nesne öğesi olarak işaretleme belirtilmesi gerekmez. Bunun yerine, koleksiyondaki öğelerin olmaya yönelik öğeleri bir veya daha fazla öğenin alt öğeleri özellik belirtilir. Her bir öğe yükleme sırasında bir nesne için değerlendirilir ve çağırarak koleksiyona eklenen `Add` yöntemi örtülü koleksiyon. Örneğin, <xref:System.Windows.Style.Triggers%2A> özelliği <xref:System.Windows.Style> özel koleksiyon türü alan <xref:System.Windows.TriggerCollection>, uygulayan <xref:System.Collections.IList>. Örneği oluşturmak gerekli olmayan bir <xref:System.Windows.TriggerCollection> biçimlendirmede nesne öğesi. Bunun yerine, bir veya daha fazla belirttiğiniz <xref:System.Windows.Trigger> öğeleri içinde öğeleri olarak `Style.Triggers` özellik öğesi burada <xref:System.Windows.Trigger> (veya türetilmiş bir sınıf) kesin türü belirtilmiş ve örtük için öğe türü olarak beklenen tür <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Bu konunun sonraki bölümünde ele alınmıştır bir özellik hem bir koleksiyon türü hem de türü için XAML içerik özelliği olabilir ve türetilmiş türler.  
  
 Bir öğe olarak biçimlendirmede görünmez olsa da bir örtülü koleksiyon öğesi mantıksal ağaç gösteriminde bir üye oluşturur. Üst türü oluşturucusuna oluşturmada özelliklerinden biri olan koleksiyon için genellikle gerçekleştirir ve başlangıçta boş bir koleksiyon nesne ağacının bir parçası haline gelir.  
  
> [!NOTE]
>  Liste ve sözlük bulunan genel arabirimleri (<xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602>) koleksiyonu algılama için desteklenmez. Ancak, kullanabileceğiniz <xref:System.Collections.Generic.List%601> uyguladığından, sınıf bir temel sınıf <xref:System.Collections.IList> doğrudan veya <xref:System.Collections.Generic.Dictionary%602> bir temel sınıf olarak uyguladığından, <xref:System.Collections.IDictionary> doğrudan.  
  
 Koleksiyon türleri için .NET başvurusu sayfalarında, bu bilinçli bir koleksiyon için nesne öğesi Java'daki sözdizimiyle örtülü koleksiyon söz dizimine XAML sözdizimi bölümlerinde bazen belirtilir.  
  
 Kök öğe dışında her nesne başka bir öğenin alt öğesi iç içe bir XAML dosyasında öğedir gerçekten birini veya ikisini de aşağıdaki durumlarda bir öğeyi: üst öğesi bir örtük toplama özelliğine üyesi , veya öğenin üst öğesi (XAML İçerik özellikleri gelecek bölümde açıklanan) için XAML İçerik özelliğinin değerini belirtir. Diğer bir deyişle, üst öğeler ve alt öğeleri bir biçimlendirme sayfasında arasındaki ilişkiyi gerçekten kökünde tek bir nesne, ise her nesne öğesi kökü altındaki üst öğesinin özellik değeri sağlayan tek bir örnek veya öğeleri bir col biri üst koleksiyon türü özellik değerini de olan seçimi. Bu tek köklü kavramı, XML ile ortak olan ve sık XAML gibi yük API'lerinin davranışı desteklenir <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Aşağıdaki örnek, bir koleksiyon için nesne öğesi sözdizimi (<xref:System.Windows.Media.GradientStopCollection>) açıkça belirtilmiş.  
  
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
  
 Bu her zaman koleksiyon açıkça bildirmek mümkün olmadığını unutmayın. Örneğin, bildirme girişiminde <xref:System.Windows.TriggerCollection> açıkça içinde daha önce gösterilen <xref:System.Windows.Style.Triggers%2A> örnek başarısız olurdu. Koleksiyon açıkça bildirme gerektirir koleksiyon sınıfı bir varsayılan oluşturucu desteklemesi gerekir ve <xref:System.Windows.TriggerCollection> bir varsayılan oluşturucuya sahip değil.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML İçerik özellikleri  
 XAML içerik sözdizimi olduğunu belirten sınıflarda yalnızca etkin bir söz dizimi <xref:System.Windows.Markup.ContentPropertyAttribute> kendi sınıf bildiriminin bir parçası olarak. <xref:System.Windows.Markup.ContentPropertyAttribute> İçerik özelliği bu tür bir öğe (türetilmiş sınıfları dahil) için özellik adını başvuruyor. XAML işlemcisi tarafından işlenen, herhangi bir alt öğeleri veya açılış ve kapanış etiketlerinin nesne öğesi arasında bulunan iç metni bu nesne için XAML İçerik özelliğinin değeri olarak atanır. İçerik özelliği için açık özellik öğeleri belirtmek için izin verilir, ancak bu kullanım genellikle .NET başvurusu XAML sözdizimi bölümlerinde gösterilen değil. Açık/verbose teknik biçimlendirme anlaşılması için veya birkaç biçimlendirme stili olarak zaman değeri var, ancak genellikle bir içerik özelliğinin amacı sezgisel üst-alt öğe ilişkili öğeleri doğrudan yuvalanabilir biçimlendirme kolaylaştırmak. Özellik öğesi etiketleri bir öğe üzerinde diğer özellikler için katı bir XAML dil tanımı; başına "içerik" olarak atanmamış Bunlar, daha önce XAML ayrıştırıcı'nın işleme sırayla işlenir ve "içerik" olmasını dikkate alınmaz.  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML İçerik özellik değerlerini bitişik olması gerekir  
 XAML İçerik özelliğinin değeri, nesne öğesi üzerinde tamamen önce veya sonra herhangi bir özellik öğe için bir tamamen verilmelidir. XAML İçerik özelliğinin değeri bir dize olarak ya da bir veya daha fazla nesne olarak belirtildiğini, bu durum geçerlidir. Örneğin, aşağıdaki biçimlendirme ayrıştırılamıyor:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Bu temelde geçersiz olduğundan bu söz dizimi içerik özelliği için özellik öğesi sözdizimi kullanarak açık yapıldıysa, ardından içerik özelliği iki kez ayarlanır:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Benzer şekilde geçersiz bir örnek, içerik özelliği bir koleksiyonudur ve alt öğelerin özellik öğeleri ile interspersed verilmiştir:  
  
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
## <a name="content-properties-and-collection-syntax-combined"></a>İçerik özellikleri ve birleştirilmiş toplama söz dizimi  
 Kabul etmek için bir tek nesne öğesi içeriği olarak birden fazla içerik özelliğinin türü özellikle bir koleksiyon türünde olmalıdır. Koleksiyon türleri için özellik öğesi sözdizimine benzer bir XAML işlemci koleksiyon türleri türlere tanımlamalıdır. Bir XAML içerik özelliği bir öğe varsa ve XAML içerik özelliği bir koleksiyon türüdür, ardından örtülü koleksiyon türü bir nesne öğesi olarak işaretleme belirtilmesi gerekmez ve XAML içerik özelliği bir özellik el belirtilmesi gerekmez. etim. Bu nedenle biçimlendirme görünen içerik modelinde artık içeriği olarak atanmış birden fazla alt öğesi olabilir. İçerik sözdizimi aşağıdaki gibidir bir <xref:System.Windows.Controls.Panel> türetilmiş sınıf. Tüm <xref:System.Windows.Controls.Panel> türetilmiş sınıflar, XAML içerik özelliği olacak şekilde kurmak <xref:System.Windows.Controls.Panel.Children%2A>, türünde bir değer gerektiren <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Unutmayın için hiçbir özellik öğesi <xref:System.Windows.Controls.Panel.Children%2A> ya da öğe için <xref:System.Windows.Controls.UIElementCollection> işaretlemede gereklidir. Yinelemeli olarak tanımlayan öğeler içeriyor. böylece bu tasarım XAML özelliğidir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] müdahalede bulunan özellik öğesi etiketleri olmadan hemen üst-alt öğe ilişkilerini ile iç içe öğe ağacındaki daha sezgisel gösterilen olan veya Koleksiyon nesnelerini. Aslında, <xref:System.Windows.Controls.UIElementCollection> tasarım gereği açıkça işaretlemede bir nesne öğesi belirtilemez. Yalnızca yaradıklarını örtük bir koleksiyon olarak olduğundan <xref:System.Windows.Controls.UIElementCollection> genel bir varsayılan oluşturucu kullanıma sunmuyor ve bu nedenle bir nesne öğesi olarak oluşturulamaz.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Özellik öğeleri ve içerik özelliğine sahip bir nesne nesne öğeleri karıştırma  
 XAML belirtimi, XAML işlemci XAML içerik özelliği bir nesne öğesi içinde doldurmak için kullanılan nesne öğelerini bitişik olmalıdır ve değil karışık olmalı zorunlu kılabilir bildirir. Bu kısıtlama, özellik öğelerinin ve içerik karıştırma karşı olarak zorunlu kılınmıştır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci.  
  
 İlk anında biçimlendirmesi içinde bir nesne öğesi olarak bir alt nesne öğesi olabilir. Özellik öğelerinin ortaya çıkarabilir. Veya, bir veya daha fazla özellik öğelerinin sonra içeriği sonra daha fazla özellik öğelerini belirtebilirsiniz. Ancak, bir özellik öğesi içeriği aşağıdaki sonra herhangi bir içerik yapamazsınız, yalnızca özellik öğeleri ekleyebilirsiniz.  
  
 Bu içerik / özellik öğe sırasını gereksinim içeriği olarak kullanılan iç metni için geçerli değildir. Ancak, yine de önemli boşluk özellik öğelerinin iç metni ile interspersed görsel olarak işaretlemede saptamak zor olabilir çünkü iç metni bitişik, tutmak için iyi biçimlendirme stili olur.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML Ad Uzayları  
 Yukarıdaki söz dizimi örnekleri hiçbiri varsayılan XAML ad alanı başka bir XAML ad alanı belirtildi. Tipik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, XAML ad alanı varsayılan olarak belirtilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ad alanı. Varsayılan XAML ad alanı dışında XAML ad alanları belirtin ve yine de benzer bir söz dizimi kullanın. Ancak daha sonra herhangi bir yerde bir sınıf, varsayılan XAML ad alanı içinde erişilebilir değil burada adlı bu sınıf adı XAML ad alanı ön ekine sahip karşılık gelen CLR ad alanına eşlenmiş olarak gelmelidir. Örneğin, `<custom:Example/>` bir örneği için nesne öğesi sözdizimi `Example` burada o sınıf (ve muhtemelen yedekleme türleri içeren dış bütünleştirilmiş kod bilgisi) içeren CLR ad alanı önceden eşlenmiş sınıfı `custom` önek.  
  
 XAML ad alanları hakkında daha fazla bilgi için bkz. [XAML ad alanları ve WPF XAML Namespace eşleme](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Biçimlendirme uzantıları  
 XAML öznitelik değerleri dize veya nesne öğe normal XAML işlemci işleme gelen kaçış dizisi sağlar ve bir yedekleme sınıfı işleme erteler varlık programlama bir işaretleme uzantısı tanımlar. XAML işlemci için bir işaretleme uzantısı özniteliği söz dizimini kullanarak bir kapatma küme ayracından (}) dışında herhangi bir karakterle ardından açma küme ayracı ({}) olduğunda tanımlayan karakter. Açılış kaşlı ayracından izleyen ilk dize, alt dizenin doğru sınıf adı bir parçası ise "Uzantısını" başvuru alt dizeyi burada atlasa belirli uzantıyı davranış sağlayan sınıf başvurmalıdır. Bundan sonra tek bir boşluk görünebilir ve kapanış küme ayracını karşılaşılanaa kadar ardından izleyen her karakter giriş olarak uzantı uygulama tarafından kullanılır.  
  
 .NET XAML uygulaması kullanan <xref:System.Windows.Markup.MarkupExtension> tüm tarafından desteklenen biçimlendirme uzantıları için temel olarak soyut sınıf [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yanı sıra diğer çerçeveleri ve teknolojileri. Biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikle uygulayan varolan nesnelerden başvuru ya da çalışma zamanında değerlendirilir nesnelere ertelenmiş başvuru yapmak için bir yol sağlamak için çoğunlukla yöneliktir. Örneğin, bir Basit WPF verilerini bağlama belirterek gerçekleştirilir `{Binding}` belirli bir özelliğin normalde götürecek değer yerine işaretleme uzantısı. WPF biçimlendirme uzantıları burada bir öznitelik sözdizimi aksi mümkün olmazdı özellikleri için bir öznitelik sözdizimi etkinleştirir. Örneğin, bir <xref:System.Windows.Style> nesnedir, iç içe geçmiş dizi nesneleri ve özellikleri içeren nispeten karmaşık bir tür. Stilleri ' WPF'de bir kaynak olarak tanımlanmış genellikle bir <xref:System.Windows.ResourceDictionary>ve bir kaynak isteği iki WPF biçimlendirme uzantıları başvuru. İşaretleme uzantısı kaynak araması özellik değerinin değerlendirme erteler ve değeri sağlama sağlayan <xref:System.Windows.FrameworkElement.Style%2A> türü alma özelliği <xref:System.Windows.Style>, öznitelik sözdizimi aşağıdaki örnekte olduğu gibi:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Burada, `StaticResource` tanımlayan <xref:System.Windows.StaticResourceExtension> işaretleme uzantısı uygulanmasını sağlayan sınıf. Sonraki dize `MyStyle` varsayılan olmayan için girdi olarak kullanılan <xref:System.Windows.StaticResourceExtension> oluşturucusu, burada uzantı dizeden alınan parametresi bildirir istenen <xref:System.Windows.ResourceKey>. `MyStyle` olması beklenir [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) değerini bir <xref:System.Windows.Style> bir kaynak olarak tanımlanır. [StaticResource işaretleme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) kullanım istekleri kaynak sağlamak için kullanılan <xref:System.Windows.Style> aracılığıyla statik kaynak arama mantığı yükleme zamanında özellik değeri.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md). İşaretleme uzantıları ve özellikleri genel .NET XAML uygulamasında etkin programlama diğer XAML başvuru için bkz: [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). WPF özel biçimlendirme uzantıları için bkz: [WPF XAML uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Ekli Özellikler  
 Ekli özellikler yapabildiği özellikler ait ve belirli bir tür tarafından tanımlanan XAML içinde tanıtılan bir programlama konsepti olan herhangi bir öğede öznitelikleri veya özelliği öğeleri olarak ancak ayarlayın. Birincil senaryo iliştirilmiş özellikler yöneliktir rapor bilgilerini bir üst öğesi için işaretleme yapısına alt öğeleri kapsamlı bir şekilde paylaşılan nesne modeli tüm öğeleri gerek kalmadan etkinleştirmektir. Buna karşılık, ekli özellikler, alt öğeleri için rapor bilgilere üst öğeler tarafından kullanılabilir. Ekli özellikler iliştirilmiş özellikler ve kendi oluşturma amacı hakkında daha fazla bilgi için bkz: [ekli özelliklere genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Ekli özelliklerini kullanma yüzeysel olarak özellik öğesi sözdizimine benzer bir sözdizimi da belirttiğiniz bir *typeName*. *propertyName* birleşimi. İki önemli farklar vardır:  
  
-   Kullanabileceğiniz *typeName*. *propertyName* birlikte öznitelik söz dizimi aracılığıyla eklenen bir özelliği ayarlamak için kullanılır. Ekli özellikler yalnızca durum özellik adı uygun yerlerde öznitelik sözdizimi içinde bir gereksinim bağımlıdır.  
  
-   Özellik öğesi sözdizimine iliştirilmiş özellikler için de kullanabilirsiniz. Ancak, tipik bir özellik öğesi sözdizimi için *typeName* özellik öğesi içeren bir nesne öğe belirtin. Ekli bir özellik için başvuruyorsanız sonra *typeName* ekli değil içeren nesne öğesi özelliği tanımlayan sınıftır.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Ekli Olaylar  
 Ekli olaylar burada olayları belirli bir tür tarafından tanımlanabilir, ancak herhangi bir nesne öğede işleyicilerinin XAML sürümünde başka bir programlama kavram olarak oldukça basittir. WOF uygulamada genellikle ekli olay tanımlayan bir hizmeti tanımlayan bir statik türü türüdür ve bazen ekli olayları yönlendirilmiş olay-diğer ad hizmeti göstermek türlerinde tarafından kullanıma sunulan. Ekli olayları için işleyiciler öznitelik sözdizimi ile belirtilmiş. Ekli olaylar ile ekli olaylar izin vermek genişletilmiş öznitelik sözdizimi gibi bir *typeName*. *eventName* kullanım, burada *typeName* sağlayan sınıfının `Add` ve `Remove` ekli olay altyapısı için olay işleyicisi erişimcileri ve *eventName* olay adı.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML kök öğe anatomisi  
 Aşağıdaki tabloda, bir kök öğenin belirli öznitelikleri gösteren aşağı bozuk tipik bir XAML kök öğesi gösterilmektedir:  
  
|||  
|-|-|  
|`<Page`|Object öğesi kök öğe açma|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Varsayılan ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML ad alanı|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML dil XAML ad alanı|  
|`x:Class="ExampleNamespace.ExampleCode"`|Tüm arka plan kod için işaretleme bağlanan kısmi sınıf bildirimi kısmi sınıf için tanımlanmış|  
|`>`|Object öğesi kök sonu. Öğe alt öğeler içerdiğinden nesnesi henüz kapalı değil|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>İsteğe bağlı ve Nonrecommended XAML kullanımları  
 Teknik olarak XAML işlemcileri tarafından desteklenen, ancak ayrıntı veya ne zaman okunabilir kalan XAML dosyalarıyla uğratabilecek diğer estetik sorunlar üretmek XAML kullanımları aşağıdaki bölümlerde, XAML kaynakları içeren uygulamalar geliştirin .  
  
### <a name="optional-property-element-usages"></a>İsteğe bağlı özellik öğesi kullanımı  
 İsteğe bağlı özellik öğesi kullanımı açıkça XAML işlemci örtük olarak değerlendirir, öğe içerik özellikleri yazma içerir. Örneğin, içeriği bildirdiğinizde bir <xref:System.Windows.Controls.Menu>, açıkça bildirmek seçebilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonunu <xref:System.Windows.Controls.Menu> olarak bir `<Menu.Items>` özellik öğesi etiketi ve yerde her <xref:System.Windows.Controls.MenuItem> içinde `<Menu.Items>`yerine örtük XAML işlemci davranışı kullanmaktan, tüm alt öğelerini bir <xref:System.Windows.Controls.Menu> olmalıdır bir <xref:System.Windows.Controls.MenuItem> ve yerleştirilir <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu. Bazen isteğe bağlı kullanımı, görsel biçimlendirme içinde temsil edilen nesne yapısını açıklamak için yardımcı olabilir. Veya bir açık özellik öğesi kullanımı görsel olarak, bir öznitelik değeri içinde iç içe geçmiş biçimlendirme uzantıları gibi kafa karıştırıcı ancak teknik işlevsel biçimlendirme bazen önleyebilirsiniz.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Tam typeName.memberName koşullu öznitelikleri  
 *TypeName*. *memberName* aslında bir öznitelik yalnızca yönlendirilmiş olay çalışması daha Evrensel çalıştığı için formu. Ancak diğer durumlarda, gereksiz biçimidir ve, varsa nedeniyle biçimlendirme stili ve okunabilirliği için yalnızca kaçınmalısınız. Aşağıdaki örnekte, her biri üç başvurular <xref:System.Windows.Controls.Control.Background%2A> özniteliği tamamen eşdeğerdir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` çalışır çünkü tam arama söz konusu özellik üzerinde için <xref:System.Windows.Controls.Button> başarılı (<xref:System.Windows.Controls.Control.Background%2A> denetiminden devralındı) ve <xref:System.Windows.Controls.Button> sınıfı nesne öğesinin veya temel sınıf. `Control.Background` çalışır çünkü <xref:System.Windows.Controls.Control> sınıfı gerçekten tanımlar <xref:System.Windows.Controls.Control.Background%2A> ve <xref:System.Windows.Controls.Control> olduğu bir <xref:System.Windows.Controls.Button> temel sınıfı.  
  
 Ancak, aşağıdaki *typeName*. *memberName* form örneği çalışmaz ve bu nedenle açıklamalı gösterilir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> başka bir türetilmiş sınıf <xref:System.Windows.Controls.Control>, ve sizin belirlemiş olsaydık `Label.Background` içinde bir <xref:System.Windows.Controls.Label> object öğesi, bu kullanım çalışmış olduğunuz. Ancak, çünkü <xref:System.Windows.Controls.Label> sınıf veya temel sınıfının değil <xref:System.Windows.Controls.Button>, belirtilen XAML işlemci davranışını ardından işlenmesidir `Label.Background` ekli özelliği olarak. `Label.Background` iliştirilmiş özellik kullanılabilir değil ve bu kullanım başarısız olur.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName özellik öğeleri  
 Benzer bir şekilde nasıl *typeName*. *memberName* form öznitelik sözdizimi için çalışan bir *baseTypeName*. *memberName* sözdizimi için özellik öğesi sözdizimine çalışır. Örneğin, aşağıdaki söz dizimini çalışır:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Özellik öğesi olarak burada verilen `Control.Background` özellik öğesi içinde yer alan olsa bile `Button`.  
  
 Ancak yalnızca *typeName*. *memberName* form öznitelikler, *baseTypeName*. *memberName* biçimlendirmede kötü stili ve kaçınmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XAML Ad Alanı (x:) Dil Özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML Uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
