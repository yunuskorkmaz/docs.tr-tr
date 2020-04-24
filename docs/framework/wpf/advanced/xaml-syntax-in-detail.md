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
ms.openlocfilehash: 5f8bb862ce443fd7397036b10f69cda65a6960bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646152"
---
# <a name="xaml-syntax-in-detail"></a>Ayrıntılı XAML Sözdizimi
Bu konu, XAML sözdizimi öğelerini açıklamak için kullanılan terimleri tanımlar. Bu terimler, hem özel olarak WPF belgeleri hem de XAML kullanan diğer çerçeveler veya System.Xaml düzeyinde XAML dil desteği tarafından etkinleştirilen temel XAML kavramları için bu belgelerin geri kalanı boyunca sık sık kullanılır. Bu [konu, XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)konusuna getirilen temel terminolojiyi genişletir.  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>XAML Dil Belirtimi  
 Burada tanımlanan XAML sözdizimi terminolojisi, XAML dil belirtimi içinde tanımlanır veya başvurulmıştır. XAML, XML'e dayalı bir dildir ve XML yapısal kurallarına uyar veya genişletir. Terminolojinin bir kısmı XML dilini veya XML belge nesnesi modelini açıklarken yaygın olarak kullanılan terminolojiden paylaşılır veya temel alınır.  
  
 XAML dil belirtimi hakkında daha fazla bilgi için Microsoft Download Center'dan [ \[\] MS-XAML'yi](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) indirin.  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML ve CLR  
 XAML bir biçimlendirme dilidir. Adının ima ettiği ortak dil çalışma zamanı (CLR), çalışma zamanının yürütülmesini sağlıyor. XAML tek başına CLR çalışma zamanı tarafından doğrudan tüketilen ortak dillerden biri değildir. Bunun yerine, XAML'yi kendi türü sistemini destekleyen olarak düşünebilirsiniz. WPF tarafından kullanılan belirli XAML ayrıştırma sistemi CLR ve CLR tipi sistem üzerine inşa edilmiştir. XAML türleri, WPF için XAML ayrıştırıldığında çalışma süresi gösterimini anında sağlamak için CLR türlerine eşlenir. Bu nedenle, XAML dil belirtiminde eşdeğer sözdizimi tartışmaları olmasa bile, bu belgede sözdizimi tartışma kalan CLR türü sistemine başvurular içerecektir. (XAML dil belirtimi düzeyine göre, XAML türleri CLR olmak zorunda olmayan başka bir tür sistemine eşlenebilir, ancak bu farklı bir XAML ayrıştırıcısının oluşturulmasını ve kullanılmasını gerektirir.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Tür ve Sınıf Devralma Üyeleri  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türün XAML üyeleri olarak göründükleri özellikler ve olaylar genellikle temel türlerden devralınır. Örneğin, şu örneği `<Button Background="Blue" .../>`göz önünde bulundurun: . Sınıf <xref:System.Windows.Controls.Control.Background%2A> tanımına, yansıma sonuçlarına <xref:System.Windows.Controls.Button> veya belgelere bakarsanız, özellik sınıfta hemen beyan edilen bir özellik değildir. Bunun <xref:System.Windows.Controls.Control.Background%2A> yerine, taban <xref:System.Windows.Controls.Control> sınıftan devralır.  
  
 XAML öğelerinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf kalıtım davranışı, XML biçimlendirmesinin şema tarafından uygulanan bir yorumundan önemli bir ayrılıştır. Sınıf kalıtım, özellikle ara temel sınıflar soyut olduğunda veya arabirimler söz konusu olduğunda karmaşık hale gelebilir. XAML öğeleri kümesinin ve bunların izin verilen özniteliklerinin, Genellikle DTD veya XSD biçimi gibi XML programlamaiçin kullanılan şema türlerini kullanarak doğru ve tamamen temsil etmesinin zor olmasının bir nedeni budur. Başka bir neden, XAML dilinin genişletilebilirlik ve tür eşleme özelliklerinin izin verilen türlerin ve üyelerin sabit gösterimlerinin eksiksizliğini engellemesidir.  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>Nesne Öğesi Sözdizimi  
 *Nesne öğesi sözdizimi,* bir XML öğesi beyan ederek bir CLR sınıfını veya yapısını anında alan XAML biçimlendirme sözdizimidir. Bu sözdizimi, HTML gibi diğer biçimlendirme dillerinin öğesine benzer. Nesne öğesi sözdizimi, bir\<sol açı ayraç ( ), hemen sınıf veya yapının tür adı anlık olarak takip başlar. Sıfır veya daha fazla boşluk tür adını izleyebilir ve nesne öğesinde sıfır veya daha fazla öznitelik de bildirilebilir ve her öznitelik adı="değer" çiftini ayıran bir veya daha fazla boşluk vardır. Son olarak, aşağıdakilerden biri doğru olmalıdır:  
  
- Öğe ve etiket, hemen dik açılı bir braket (>) ile birlikte bir ileri eğik çizgi (/) tarafından kapatılmalıdır.  
  
- Açılış etiketi dik açı braketi (>) ile tamamlanmalıdır. Diğer nesne öğeleri, özellik öğeleri veya iç metin, açılış etiketini izleyebilir. Burada tam olarak hangi içeriğin bulunabileceği genellikle öğenin nesne modeli tarafından kısıtlanır. Nesne öğesi için eşdeğer kapanış etiketi de, uygun yuvalama ve diğer açılış ve kapanış etiket çiftleri ile denge de olmalıdır.  
  
 .NET tarafından uygulanan XAML, nesne öğelerini türlere, özelliklere veya olaylara öznitelik ve XAML ad alanlarını CLR ad boşlukları artı derlemeye eşleyen bir kural kümesine sahiptir. WPF ve .NET için XAML nesne öğeleri, başvurulan derlemelerde tanımlandığı gibi .NET türleri ile eşleştirilir ve bu tür lerin öznitelikleri eşlenir. XAML'de bir CLR türüne başvururken, bu türdeki devralınan üyelere de erişebilirsiniz.  
  
 Örneğin, aşağıdaki örnek, <xref:System.Windows.Controls.Button> sınıfın yeni bir örneğini anında alan ve aynı zamanda bu <xref:System.Windows.FrameworkElement.Name%2A> öznitelik için bir öznitelik ve değer belirten nesne öğesi sözdizimidir:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Aşağıdaki örnek, XAML içerik özelliği sözdizimini de içeren nesne öğesi sözdizimidir. İç metin içinde XAML içerik <xref:System.Windows.Controls.TextBox> özelliğini ayarlamak <xref:System.Windows.Controls.TextBox.Text%2A>için kullanılacaktır.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>İçerik Modelleri  
 Bir sınıf sözdizimi açısından XAML nesne öğesi olarak kullanımını destekleyebilir, ancak bu öğe yalnızca genel içerik modeli veya öğe ağacının beklenen bir konuma yerleştirildiğinde bir uygulamada veya sayfada düzgün çalışır. Örneğin, a <xref:System.Windows.Controls.MenuItem> genellikle yalnızca türemiş bir <xref:System.Windows.Controls.Primitives.MenuBase> sınıfın alt <xref:System.Windows.Controls.Menu>çocuğu olarak yerleştirilmelidir. Belirli öğelere ait içerik modelleri, denetimler ve XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri olarak kullanılabilecek diğer sınıflar için sınıf sayfalarındaki açıklamaların bir parçası olarak belgelenir.  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>Nesne Öğelerinin Özellikleri  
 XAML'deki özellikler çeşitli olası sözdizimilerle ayarlanır. Belirli bir özellik için hangi sözdiziminin kullanılabileceğini, ayarladığınız özelliğin temel tür sistem özelliklerine bağlı olarak değişir.  
  
 Özelliklerin değerlerini ayarlayarak, nesnelerin çalışma zamanı nesnesi grafiğinde var oldukları gibi özellikler veya özellikler eklersiniz. Nesne öğesinden oluşturulan nesnenin ilk durumu parametresiz yapıcı davranışı temel alıncaya dayanır. Genellikle, uygulamanız herhangi bir nesnenin tamamen varsayılan örneği dışında bir şey kullanır.  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>Öznitelik Sözdizimi (Özellikler)  
 Öznitelik sözdizimi, varolan bir nesne öğesi üzerinde bir öznitelik beyan ederek bir özellik için değer ayarlayan XAML biçimlendirme sözdizimidir. Öznitelik adı, ilgili nesne öğeöğesini destekleyen sınıfın özelliğinin CLR üye adı ile eşleşmelidir. Öznitelik adı bir atama işleci (=) tarafından takip edilir. Öznitelik değeri, tırnak içinde bir dize olmalıdır.  
  
> [!NOTE]
> Bir öznitelik içinde bir edebi tırnak işareti yerleştirmek için alternatif tırnak kullanabilirsiniz. Örneğin, içinde çift tırnak karakteri içeren bir dize yi bildirmek için tek tırnak işaretini bir araç olarak kullanabilirsiniz. İster tek ister çift tırnak kullanın, öznitelik değer dizesini açmak ve kapatmak için eşleşen bir çift kullanmanız gerekir. Ayrıca kaçış dizileri veya karakter kısıtlamaları herhangi bir XAML sözdizimi tarafından dayatılan etrafında çalışmak için kullanılabilir diğer teknikler vardır. [Bkz. XML Karakter Varlıkları ve XAML.](../../../desktop-wpf/xaml-services/xml-character-entities.md)  
  
 Öznitelik sözdizimi ile ayarlanabilmesi için, bir özelliğin herkese açık olması ve yazılabilir olması gerekir. Destek türü sistemindeki özelliğin değeri bir değer türü olmalıdır veya ilgili destek türüne erişirken bir XAML işlemcisi tarafından anında lanse edilebilen veya başvurulan bir başvuru türü olmalıdır.  
  
 WPF XAML olayları için, öznitelik adı olarak başvurulan olayın herkese açık olması ve genel bir temsilciye sahip olması gerekir.  
  
 Özellik veya olay, içeren nesne öğesi tarafından anında bulunan sınıfın veya yapının bir üyesi olmalıdır.  
  
### <a name="processing-of-attribute-values"></a>Öznitelik Değerlerinin İşlenmesi  
 Açılış ve kapanış tırnak işaretleri içinde yer alan dize değeri bir XAML işlemci tarafından işlenir. Özellikler için varsayılan işleme davranışı, temel CLR özelliğinin türüne göre belirlenir.  
  
 Öznitelik değeri, bu işlem sırasını kullanarak aşağıdakilerden biri tarafından doldurulur:  
  
1. XAML işlemci kıvırcık bir ayraç la karşılaşırsa veya <xref:System.Windows.Markup.MarkupExtension>türetilen bir nesne öğesi, sonra başvurulan biçimlendirme uzantısı önce bir dize olarak değer işleme yerine değerlendirilir ve biçimlendirme uzantısı tarafından döndürülen nesne değer olarak kullanılır. Çoğu durumda biçimlendirme uzantısı tarafından döndürülen nesne, varolan bir nesneye başvuru veya değerlendirmeyi çalışma süresine kadar erteleyen ve yeni anlık bir nesne olmayan bir ifade olacaktır.  
  
2. Özellik atfedilen <xref:System.ComponentModel.TypeConverter>bir özellik ile bildirilirse veya bu özelliğin değer türü atfedilen <xref:System.ComponentModel.TypeConverter>bir şekilde bildirilirse, özniteliğin dize değeri dönüşüm girişi olarak tür dönüştürücüye gönderilir ve dönüştürücü yeni bir nesne örneği döndürür.  
  
3. Yoksa, <xref:System.ComponentModel.TypeConverter>özellik türüne doğrudan dönüştürme girişiminde bulunulr. Bu son düzey, XAML dili ilkel türleri arasındaki parser-yerel değeri doğrudan dönüştürme veya bir numaralandırma (parser sonra eşleşen değerlere erişen) adlı sabitlerin adları için bir denetim.  
  
#### <a name="enumeration-attribute-values"></a>Numaralandırma Öznitelik Değerleri  
 XAML'deki numaralandırmalar XAML ayrıştırıcıları tarafından özünde işlenir ve numaralandırmanın üyeleri numaralandırmanın adlandırılmış sabitlerinden birinin dize adı belirtilerek belirtilmelidir.  
  
 Bayrak olmayan numaralandırma değerleri için, yerel davranış bir öznitelik değeri dizesini işlemek ve numaralandırma değerlerinden birine çözmektir. Numaralandırma biçiminde *numaralandırma*yı belirtmezsiniz. *Değer*, kod da yaptığınız gibi. Bunun yerine, yalnızca *Değer'i*belirtirsiniz ve *Numaralandırma* ayarladığınız özelliğin türüne göre çıkarılır. *Numaralandırma'da*bir öznitelik belirtirseniz. *Değer* formu, doğru çözülmez.  
  
 Bayrak açısından sayısallaştırmalar için davranış yönteme <xref:System.Enum.Parse%2A?displayProperty=nameWithType> dayanır. Her değeri virgülle ayırarak, bayrak yönünden numaralandırma için birden çok değer belirtebilirsiniz. Ancak, bayrak yönünde olmayan numaralandırma değerlerini birleştiremezsiniz. Örneğin, bayrak dışı numaralandırmanın birden çok koşulunda hareket eden bir <xref:System.Windows.Trigger> sözcük oluşturmaya çalışmak için virgül sözdizimini kullanamazsınız:  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML'de ayarlanabilen öznitelikleri destekleyen bayrak yönünden yapılan sayısallaştırmalar WPF'de nadirdir. Ancak, böyle bir numaralandırma <xref:System.Windows.Media.StyleSimulations>. Örneğin, <xref:System.Windows.Documents.Glyphs> sınıf için Açıklamalar'ta sağlanan örneği değiştirmek için virgülle sınırlandırılmış bayrak özniteliği sözdizimini kullanabilirsiniz; `StyleSimulations = "BoldSimulation"` olabilir. `StyleSimulations = "BoldSimulation,ItalicSimulation"` <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>birden fazla numaralandırma değerinin belirtilebileceği başka bir özelliktir. Ancak, numaralandırma kendi türü dönüştürücü <xref:System.Windows.Input.ModifierKeys> destekler, çünkü bu özellik özel bir durum olur. Değiştiriciler için tür dönüştürücü virgül (,) yerine delimiter olarak artı işareti (+) kullanır. Bu dönüştürme, Microsoft Windows programlamada "Ctrl+Alt" gibi anahtar birleşimlerini temsil edecek daha geleneksel sözdizimini destekler.  
  
### <a name="properties-and-event-member-name-references"></a>Özellikler ve Etkinlik Üye Adı Referansları  
 Bir öznitelik belirtirken, içeren nesne öğesi için anında belirttiğiniz CLR türünün bir üyesi olarak var olan herhangi bir özelliğe veya olaya başvuruda bulunabilirsiniz.  
  
 Veya, içeren nesne öğesinden bağımsız olarak ekli bir özellik veya ekli olaya başvuruda bulunabilirsiniz. (Ekli özellikler yaklaşan bir bölümde ele alınmıştır.)  
  
 Ayrıca, varsayılan ad alanı üzerinden erişilebilen herhangi bir nesneden herhangi bir olayı *bir tür Adı*kullanarak adlandırabilirsiniz. *olay* kısmen nitelikli isim; bu sözdizimi, işleyicinin alt öğelerden yönlendirilen olayları işlemek için amaçlandığı yönlendirilmiş olaylar için işleyicileri eklemeyi destekler, ancak üst öğenin de bu olay üye tablosunda yoktur. Bu sözdizimi ekli bir olay sözdizimini andırır, ancak buradaki olay gerçek bir bağlı olay değildir. Bunun yerine, nitelikli bir ada sahip bir olaya başvuruyorsunuz. Daha fazla bilgi için, [Yönlendirilen Olaylara Genel Bakış'a](routed-events-overview.md)bakın.  
  
 Bazı senaryolar için özellik adları bazen öznitelik adı yerine öznitelik değeri olarak sağlanır. Bu özellik adı, form *sahibiType'ta*belirtilen özellik gibi niteleyicileri de içerebilir. *dependencyPropertyName*. Bu senaryo, XAML'de stilleri veya şablonları yazarken yaygındır. Öznitelik değeri olarak sağlanan özellik adlarının işleme kuralları farklıdır ve ayarlanan özelliğin türüne veya belirli WPF alt sistemlerinin davranışlarına göre yönetilir. Ayrıntılar için [Stil ve Templating'e](../../../desktop-wpf/fundamentals/styles-templates-overview.md)bakın.  
  
 Özellik adları için başka bir kullanım, bir öznitelik değeri bir özellik-özellik ilişkisini açıklar. Bu özellik veri bağlama ve film şeridi hedefleri için <xref:System.Windows.PropertyPath> kullanılır ve sınıf ve türü dönüştürücü tarafından etkinleştirilir. Arama semantikdaha eksiksiz bir açıklama için, [PropertyPath XAML Sözdizimi](propertypath-xaml-syntax.md)bakın.  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>Özellik Öğesi Sözdizimi  
 *Özellik öğesi sözdizimi,* öğeler için temel XML sözdizimi kurallarından biraz farklı olan bir sözdizimidir. XML'de, bir özniteliğin değeri fiili bir dizedir ve tek olası varyasyon dize kodlama biçiminin kullanıldığıdır. XAML'de, diğer nesne öğelerini bir özelliğin değeri olarak atayabilirsiniz. Bu özellik öğesi sözdizimi tarafından etkinleştirilir. Öğe etiketiiçinde bir öznitelik olarak belirtilen özellik yerine, özellik *öğeTypeName*bir açılış öğesi etiketi kullanılarak belirtilir. *propertyName* formu, özelliğin değeri içinde belirtilir ve sonra özellik öğesi kapatılır.  
  
 Özellikle, sözdizimi, özellik öğesi\<sözdiziminin içerdiği sınıfın veya yapının tür adı ile hemen takip edilen sol açılı bir parantezle başlar. Bunu hemen tek bir nokta (.), sonra bir özellik adı, ardından dik açılı bir köşeli ayraç (>) takip eder. Öznitelik sözdiziminde olduğu gibi, bu özellik belirtilen türdeki beyan edilen kamu üyeleri içinde bulunmalıdır. Özelliğe atanacak değer özellik öğesi içinde yer almaktadır. Nesneleri değer olarak belirtmek özellik öğesi sözdiziminin ele alınması amaçlandığı senaryo olduğundan, genellikle değer bir veya daha fazla nesne öğesi olarak verilir. Son olarak, aynı *öğetypename*belirten eşdeğer bir kapanış etiketi . *propertyName* kombinasyonu, uygun iç içe geçme ve diğer öğe etiketleri ile denge sağlanmalıdır.  
  
 Örneğin, aşağıdaki bir <xref:System.Windows.FrameworkElement.ContextMenu%2A> <xref:System.Windows.Controls.Button>özelliği için özellik öğesi sözdizimi .  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Özellik öğesi içindeki değer, özellik türünün belirtildiği ilkel bir değer türü veya bir adın <xref:System.String>belirtildiği numaralandırma gibi durumlarda iç metin olarak da verilebilir. Bu durumların her biri de daha basit bir öznitelik sözdizimi kullanabilirsiniz, çünkü bu iki kullanımları biraz nadirdir. Bir özellik öğesini dizeyle doldurmak için bir senaryo, XAML içerik özelliği olmayan ancak yine de Kullanıcı Arabirimi metninin gösterimi için kullanılan özellikler içindir ve bu kullanıcı arabirimi metninde görünmesi için satır akışları gibi belirli beyaz alan öğeleri nin görünmesi gerekir. Öznitelik sözdizimi satır beslemelerini koruyamaz, ancak özellik öğesi sözdizimi, önemli beyaz alan koruması etkin olduğu sürece bunu yapabilir (ayrıntılar için Bkz. [XAML'deki Beyaz alan işleme).](../../../desktop-wpf/xaml-services/white-space-processing.md) Başka bir senaryo, [x:Uid](../../../desktop-wpf/xaml-services/xuid-directive.md) Yönergesi'nin özellik öğesine uygulanabilmesi ve böylece içindeki değeri WPF çıktısı BAML'de veya diğer tekniklerde yerelleştirilmesi gereken bir değer olarak işaretlemesidir.  
  
 Özellik öğesi WPF mantıksal ağacında temsil edilmez. Özellik öğesi, bir özelliği ayarlamak için yalnızca belirli bir sözdizimidir ve onu destekleyen bir örneği veya nesnesi olan bir öğe değildir. (Mantıksal ağaç kavramı yla ilgili ayrıntılar için [WPF'deki Ağaçlar'a](trees-in-wpf.md)bakın.)  
  
 Hem öznitelik hem de özellik öğesi sözdiziminin desteklendiği özellikler için, beyaz boşluk işleme gibi incelikler sözdizimi arasında biraz farklılık gösterse de, iki sözdizimi genellikle aynı sonuca sahiptir.  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>Koleksiyon Sözdizimi  
 XAML belirtimi, değer türünün bir koleksiyon olduğu özellikleri tanımlamak için XAML işlemci uygulamalarını gerektirir. .NET'teki genel XAML işlemci uygulaması yönetilen kodu ve CLR'yi temel alır ve aşağıdakilerden biri aracılığıyla toplama türlerini tanımlar:  
  
- Türü <xref:System.Collections.IList>uygular.  
  
- Türü <xref:System.Collections.IDictionary>uygular.  
  
- Tür türetilmiştir <xref:System.Array> (XAML dizileri hakkında daha fazla bilgi için, [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)bakın .)  
  
 Bir özellik türü bir koleksiyon ise, o zaman çıkarılan toplama türü bir nesne öğesi olarak biçimlendirme belirtilmesi gerekmez. Bunun yerine, koleksiyondaki öğeler olması amaçlanan öğeler özellik öğesinin bir veya daha fazla alt öğesi olarak belirtilir. Bu tür her öğe yükleme sırasında bir nesneye değerlendirilir `Add` ve zımni toplama yöntemi çağırılarak koleksiyona eklenir. Örneğin, <xref:System.Windows.Style.Triggers%2A> özel <xref:System.Windows.Style> leştirilmiş toplama türünü <xref:System.Windows.TriggerCollection> <xref:System.Collections.IList>alır, hangi uygular. Biçimlendirmede bir <xref:System.Windows.TriggerCollection> nesne öğesini anında işaretlemeye gerek yoktur. Bunun <xref:System.Windows.Trigger> yerine, `Style.Triggers` <xref:System.Windows.Trigger> özellik öğesi içinde bir veya daha fazla öğeyi, (veya türetilmiş sınıf) güçlü bir şekilde <xref:System.Windows.TriggerCollection>yazılan ve örtülü olarak madde türü olarak beklenen tür olarak belirtirsiniz.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Özellik, bu tür ve bu konunun sonraki bölümünde tartışılan tür ve türiçin hem koleksiyon türü hem de XAML içerik özelliği olabilir.  
  
 Örtük bir koleksiyon öğesi, biçimlendirmede bir öğe olarak görünmese bile mantıksal ağaç gösteriminde bir üye oluşturur. Genellikle üst türün oluşturucusu, özelliklerinden biri olan koleksiyon için anlık oluşturma gerçekleştirir ve başlangıçta boş toplama nesne ağacının bir parçası olur.  
  
> [!NOTE]
> Genel liste ve sözlük<xref:System.Collections.Generic.IList%601> arabirimleri ( ve <xref:System.Collections.Generic.IDictionary%602>) toplama algılama için desteklenmez. Ancak, <xref:System.Collections.Generic.List%601> sınıfı doğrudan veya doğrudan uygulandığıiçin <xref:System.Collections.IList> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.IDictionary> taban sınıf olarak veya taban sınıf olarak kullanabilirsiniz.  
  
 Koleksiyon türleri için .NET Başvuru sayfalarında, bir koleksiyon için nesne öğesinin kasıtlı ihmali olan bu sözdizimi bazen XAML sözdizimi bölümlerinde Örtülü Koleksiyon Sözdizimi olarak belirtilir.  
  
 Kök öğesi dışında, başka bir öğenin alt öğesi olarak iç içe geçen bir XAML dosyasındaki her nesne öğesi gerçekten aşağıdaki durumlardan biri veya her ikisi olan bir öğedir: üst öğenin örtülü toplama özelliğinin bir üyesi veya üst öğe için XAML içerik özelliğinin değerini belirten bir öğe (XAML içerik özellikleri yaklaşan bir bölümde ele alınacaktır). Başka bir deyişle, biçimlendirme sayfasındaki üst öğeler ve alt öğelerin ilişkisi gerçekten kökteki tek bir nesnedir ve kökün altındaki her nesne öğesi, üst öğenin özellik değerini sağlayan tek bir örnektir veya üst öğenin koleksiyon türünde bir özellik değeri olan öğelerden biridir. Bu tek köklü kavram XML ile ortaktır ve sık sık XAML gibi <xref:System.Windows.Markup.XamlReader.Load%2A>yükleyin API'lerin davranışında takviye edilir.  
  
 Aşağıdaki örnek, bir koleksiyon için nesne öğesi<xref:System.Windows.Media.GradientStopCollection>( ) açıkça belirtilen bir sözdizimidir.  
  
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
  
 Koleksiyonu açıkça beyan etmek her zaman mümkün değildir. Örneğin, daha önce <xref:System.Windows.TriggerCollection> gösterilen <xref:System.Windows.Style.Triggers%2A> örnekte açıkça beyan etmeye çalışmak başarısız olur. Koleksiyonu açıkça bildirmek, koleksiyon sınıfının parametresiz bir oluşturucuyu <xref:System.Windows.TriggerCollection> desteklemesi gerektiğini ve parametresiz bir oluşturucusu olmamasını gerektirir.  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>XAML İçerik Özellikleri  
 XAML içerik sözdizimi, yalnızca sınıf bildirimlerinin bir <xref:System.Windows.Markup.ContentPropertyAttribute> parçası olarak belirten sınıflarda etkinleştirilmiş bir sözdizimidir. Bu <xref:System.Windows.Markup.ContentPropertyAttribute> tür bir öğenin içerik özelliği olan özellik adına (türetilmiş sınıflar dahil) başvurur. Bir XAML işlemcisi tarafından işlendiğinde, nesne öğesinin açılış ve kapanış etiketleri arasında bulunan alt öğeler veya iç metin, o nesne için XAML içerik özelliğinin değeri olarak atanır. İçerik özelliği için açık özellik öğeleri belirtmenize izin verilir, ancak bu kullanım genellikle .NET başvurusundaki XAML sözdizimi bölümlerinde gösterilmez. Açık/ayrıntılı teknik, biçimlendirme netliği için ara sıra veya biçimlendirme stili açısından zaman zaman değere sahiptir, ancak genellikle bir içerik özelliğinin amacı, üst-alt öğe olarak sezgisel olarak ilişkili öğelerin doğrudan iç içe olması için biçimlendirmeyi kolaylaştırmaktır. Bir öğedeki diğer özellikler için özellik öğesi etiketleri, katı bir XAML dil tanımına göre "içerik" olarak atanmaz; daha önce XAML ayrıştırıcısının işlem sırasına göre işlenir ve "içerik" olarak kabul edilmez.  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML İçerik Özellik Değerleri Bitişik Olmalıdır  
 Bir XAML içerik özelliğinin değeri, bu nesne öğesindeki diğer özellik öğelerinden önce veya sonra tamamen verilmelidir. Bu, bir XAML içerik özelliğinin değerinin dize olarak mı yoksa bir veya daha fazla nesne olarak mı belirtilmiş olduğu doğrudur. Örneğin, aşağıdaki biçimlendirme ayrışmaz:  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Bu, içerik özelliği için özellik öğesi sözdizimi kullanılarak açık hale getirildi, çünkü bu temelde yasadışı, o zaman içerik özelliği iki kez ayarlanır:  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Benzer şekilde yasadışı bir örnek, içerik özelliğinin bir koleksiyon olması ve alt öğelerin özellik öğeleriyle serpiştirilmiş olmasıdır:  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>
## <a name="content-properties-and-collection-syntax-combined"></a>İçerik Özellikleri ve Koleksiyon Sözdizimi Birleştirildi  
 Birden fazla nesne öğeöğesini içerik olarak kabul edebilmek için, içerik özelliğinin türü özellikle bir toplama türü olmalıdır. Koleksiyon türleri için özellik öğesi sözdizimine benzer şekilde, Bir XAML işlemcinin koleksiyon türleri olan türleri tanımlaması gerekir. Bir öğenin XAML içerik özelliği varsa ve XAML içerik özelliğinin türü bir koleksiyonsa, zımni toplama türünün biçimlendirmede nesne öğesi olarak belirtilmesi gerekmez ve XAML içerik özelliğinin özellik öğesi olarak belirtilmesi gerekmez. Bu nedenle biçimlendirmedeki görünen içerik modeliartık içerik olarak atanmış birden fazla alt öğeye sahip olabilir. Aşağıda türemiş bir <xref:System.Windows.Controls.Panel> sınıf için içerik sözdizimi veremiş tir. Tüm <xref:System.Windows.Controls.Panel> türetilmiş sınıflar, türünde <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.UIElementCollection>bir değer gerektiren XAML içerik özelliğini kurar.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Biçimlendirmede ne özellik <xref:System.Windows.Controls.Panel.Children%2A> öğesinin ne <xref:System.Windows.Controls.UIElementCollection> de öğenin gerekli olmadığını unutmayın. Bu, xaml'ın bir tasarım özelliğidir, böylece bir öğeyi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tanımlayan özyinelemeli olarak bulunan öğeler, özellik öğesi etiketleri veya koleksiyon nesnelerine müdahale etmeden, hemen üst-alt öğe ilişkileri olan iç içe geçmiş öğelerin bir ağacı olarak daha sezgisel olarak temsil edilir. Aslında, <xref:System.Windows.Controls.UIElementCollection> tasarım gereği, bir nesne öğesi olarak biçimlendirme açıkça belirtilemez. Tek kullanım alanı örtülü bir koleksiyon <xref:System.Windows.Controls.UIElementCollection> olduğundan, genel parametresiz bir oluşturucu yu teşrelemez ve bu nedenle nesne öğesi olarak anında alınamaz.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Özellik Öğelerini ve Nesne Öğelerini İçerik Özelliğiyle Nesne'de Karıştırma  
 XAML belirtimi, bir XAML işlemcinin, bir nesne öğesi içindeki XAML içerik özelliğini doldurmak için kullanılan nesne öğelerinin bitişik olması gerektiğini ve karıştırılmaması gerektiğini zorladığını bildirir. Özellik öğelerive içeriği karıştırmaya karşı bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kısıtlama XAML işlemciler tarafından uygulanır.  
  
 Bir alt nesne öğesi, nesne öğesi içindeki ilk anlık biçimlendirme olarak sahip olabilirsiniz. Sonra özellik öğeleri tanıtabilirsiniz. Veya, bir veya daha fazla özellik öğeleri, sonra içerik, daha sonra daha fazla özellik öğeleri belirtebilirsiniz. Ancak bir özellik öğesi içeriği takip ettikten sonra, başka içerik tanıtamazsınız, yalnızca özellik öğeleri ekleyebilirsiniz.  
  
 Bu içerik / özellik öğesi sipariş gereksinimi içerik olarak kullanılan iç metin için geçerli değildir. Ancak, özellik öğeleri iç metin serpiştirilmiş ise önemli beyaz boşluk biçimlendirme görsel olarak algılamak zor olacaktır, çünkü iç metin bitişik tutmak için hala iyi bir biçimlendirme stilidir.  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>XAML Ad Uzayları  
 Önceki sözdizimi örneklerinin hiçbiri varsayılan XAML ad alanı dışında bir XAML ad alanı belirtmedi. Tipik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarda, varsayılan XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ad alanı ad alanı olarak belirtilir. Varsayılan XAML ad alanı dışında XAML ad alanları belirtebilir ve yine de benzer sözdizimi kullanabilirsiniz. Ancak, varsayılan XAML ad alanı içinde erişilemeyen bir sınıfın adlandırılmasının yapıldığı her yerde, bu sınıf adının, ilgili CLR ad alanına eşlenen XAML ad alanının önekiyle önce olması gerekir. Örneğin, `<custom:Example/>` sınıfın bir örneğini `Example` anında anımsa, bu sınıfı içeren CLR ad alanının (ve muhtemelen destek türlerini içeren dış derleme `custom` bilgilerinin) daha önce önek eşlendiği nesne öğesi sözdizimidir.  
  
 XAML ad alanları hakkında daha fazla bilgi için [WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemi'ne](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>İşaretleme Uzantıları  
 XAML, dize öznitelik değerlerinin veya nesne öğelerinin normal XAML işlemci işlemesinden kaçışı sağlayan bir biçimlendirme uzantısı programlama varlığı tanımlar ve işlemeyi bir destek sınıfına erteler. Öznitelik sözdizimi kullanırken XAML işlemciiçin biçimlendirme uzantısı tanımlayan karakter, açılış kıvırcık ayracıdır ({), ardından kapanış kıvırcık ayracı (}) dışındaki herhangi bir karakter. Açılış kıvırcık ayracını izleyen ilk dize, bu alt dize gerçek sınıf adının bir parçasıysa, başvurunun "Uzantı" alt dizesini atlayabildiği belirli uzantı davranışını sağlayan sınıfa başvurmalıdır. Bundan sonra, tek bir boşluk görünebilir ve ardından her başarılı karakter, kapanış kıvırcık ayracı karşılaşılana kadar uzantı uygulaması tarafından giriş olarak kullanılır.  
  
 .NET XAML uygulaması, <xref:System.Windows.Markup.MarkupExtension> soyut sınıfı, diğer çerçeveler veya teknolojilerin yanı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıra desteklenen tüm biçimlendirme uzantıları için temel olarak kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellikle uygulanan biçimlendirme uzantıları genellikle diğer varolan nesnelere başvuru yapmak veya çalışma zamanında değerlendirilecek nesnelere ertelenmiş başvurular yapmak için bir araç sağlamak için tasarlanmıştır. Örneğin, belirli bir özelliğin `{Binding}` normalde alacağı değer yerine biçimlendirme uzantısı belirtilerek basit bir WPF veri bağlama gerçekleştirilir. WPF biçimlendirme uzantılarının çoğu, öznitelik sözdiziminin başka türlü mümkün olmadığı özellikler için bir öznitelik sözdizimini etkinleştirin. Örneğin, bir <xref:System.Windows.Style> nesne, iç içe nesneler ve özellikler dizisi içeren nispeten karmaşık bir türdür. WPF'deki stiller genellikle bir <xref:System.Windows.ResourceDictionary>kaynak olarak tanımlanır ve kaynak isteyen iki WPF biçimlendirme uzantısından biri aracılığıyla başvurur. Biçimlendirme uzantısı, özellik değerinin bir kaynak aramasına değerlendirilmesini erteler ve aşağıdaki <xref:System.Windows.FrameworkElement.Style%2A> örnekte <xref:System.Windows.Style>olduğu gibi özellik değerini nitrek, tür alarak, özelliğin değerini sağlamanızı sağlar:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Burada, `StaticResource` biçimlendirme uzantısı uygulamasını sağlayan <xref:System.Windows.StaticResourceExtension> sınıfı tanımlar. Sonraki dize, `MyStyle` uzantı dizesinden alınan <xref:System.Windows.StaticResourceExtension> parametrenin isteneni bildirdiği varsayılan olmayan oluşturucu için <xref:System.Windows.ResourceKey>giriş olarak kullanılır. `MyStyle`kaynak olarak tanımlanan bir <xref:System.Windows.Style> [x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) değeri olması beklenmektedir. [StaticResource Biçimlendirme Uzantısı](staticresource-markup-extension.md) kullanımı, kaynağın yük <xref:System.Windows.Style> zamanında statik kaynak arama mantığı aracılığıyla özellik değerini sağlamak için kullanılmasını ister.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için [bkz.](markup-extensions-and-wpf-xaml.md) Genel .NET XAML uygulamasında etkin biçimlendirme uzantıları ve diğer XAML programlama özelliklerine başvuru için [bkz. Dil Özellikleri](../../../desktop-wpf/xaml-services/namespace-language-features.md). WPF'ye özgü biçimlendirme uzantıları için [Bkz. WPF XAML Uzantıları.](wpf-xaml-extensions.md)  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>Ekli Özellikler  
 Ekli özellikler, xaml'da tanıtılan ve özelliklerin belirli bir türtarafından sahiplenilebildiği ve tanımlanabileceği, ancak herhangi bir öğedeki öznitelikler veya özellik öğeleri olarak ayarlanabilen bir programlama kavramıdır. Ekli özelliklerin amaçlandığı birincil senaryo, biçimlendirme yapısındaki alt öğelerin tüm öğeler arasında kapsamlı olarak paylaşılan bir nesne modeline gerek kalmadan bilgileri bir üst öğeye bildirmesini sağlamaktır. Tersine, ekli özellikler alt öğelere bilgi raporlamak için üst öğeler tarafından kullanılabilir. Ekli özelliklerin amacı ve kendi eklenmiş özelliklerinizin nasıl oluşturulması hakkında daha fazla bilgi [için](attached-properties-overview.md)bkz.  
  
 Eklenen özellikler, özellik öğesi sözdizimini yüzeysel olarak andıran bir sözdizimi kullanır, bu da bir *tür Adı*belirtirsiniz. *propertyName* kombinasyonu. İki önemli fark vardır:  
  
- *TypeName'i*kullanabilirsiniz. *özellikÖzsöz* dizini aracılığıyla ekli bir özellik ayarlarken bile ad birleşimi. Ekli özellikler, özellik adını nitelemenin bir öznitelik sözdiziminde bir gereklilik olduğu tek durumdur.  
  
- Ekli özellikler için özellik öğesi sözdizimini de kullanabilirsiniz. Ancak, tipik özellik öğesi sözdizimi için, belirttiğiniz *tür Adı* özellik öğesini içeren nesne öğesidir. Ekli bir özelliğe başvuruyorsanız, *typeName,* içeren nesne öğe öğesini değil, ekli özelliği tanımlayan sınıftır.  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>Ekli Olaylar  
 Ekli olaylar, XAML'de tanıtılan ve olayların belirli bir türle tanımlanabildiği, ancak işleyicilerin herhangi bir nesne öğesine eklenebileceği başka bir programlama kavramıdır. WOF uygulamasında, genellikle ekli bir olayı tanımlayan tür, bir hizmeti tanımlayan statik bir türdür ve bazen bu eklenen olaylar, hizmeti ortaya çıkaran türlerde yönlendirilmiş olay takma adı tarafından ortaya çıkar. Ekli olaylar için işleyicileri öznitelik sözdizimi ile belirtilir. Ekli olaylarda olduğu gibi, öznitelik sözdizimi ekli olaylar için bir *tür Adına*izin vermek üzere genişletilir. *eventName* kullanımı, *typeName'in* bağlı `Add` `Remove` olay altyapısı için etkinlik işleyicisi erişimsağlayan sınıf olduğu ve *eventName'nin* olay adı olduğu.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>XAML Kök Elementinin Anatomisi  
 Aşağıdaki tablo, bir kök öğenin belirli özniteliklerini gösteren, ayrılmış tipik bir XAML kök öğesini gösterir:  
  
|||  
|-|-|  
|`<Page`|Kök öğenin nesne öğesini açma|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Varsayılan ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML ad alanı|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML dili XAML ad alanı|  
|`x:Class="ExampleNamespace.ExampleCode"`|Biçimlendirmeyi kısmi sınıf için tanımlanan herhangi bir kod arkasına bağlayan kısmi sınıf bildirimi|  
|`>`|Kök için nesne öğesinin sonu. Öğe alt öğeleri içerdiğinden nesne henüz kapalı değil|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>İsteğe bağlı ve Tavsiye Edilmeyen XAML Kullanımları  
 Aşağıdaki bölümlerde, XAML işlemciler tarafından teknik olarak desteklenen, ancak XAML kaynakları içeren uygulamalar geliştirdiğinizde insan tarafından okunabilir kalan XAML dosyalarını engelleyen ayrıntılılık veya diğer estetik sorunlar üreten XAML kullanımları açıklanmaktadır.  
  
### <a name="optional-property-element-usages"></a>İsteğe Bağlı Özellik Öğesi Kullanımları  
 İsteğe bağlı özellik öğesi kullanımları, XAML işlemcinin örtülü olarak gördüğü öğe içeriği özelliklerini açıkça yazmayı içerir. <xref:System.Windows.Controls.Menu>Örneğin, bir , bir <xref:System.Windows.Controls.ItemsControl.Items%2A> , bir tüm alt öğeleri a <xref:System.Windows.Controls.Menu> `<Menu.Items>` <xref:System.Windows.Controls.MenuItem> `<Menu.Items>` <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.MenuItem> olması gereken ve <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyona yerleştirilir örtülü XAML işlemci davranışını kullanarak yerine, bir özellik öğesi etiketi olarak toplama açıkça beyan etmek ve her birini yerleştirebilirsiniz. Bazen isteğe bağlı kullanımlar, biçimlendirmede temsil edilen nesne yapısını görsel olarak netleştirmeye yardımcı olabilir. Veya bazen açık bir özellik öğesi kullanımı, öznitelik değeri içindeki iç içe biçimlendirme uzantıları gibi teknik olarak işlevsel ancak görsel olarak kafa karıştırıcı biçimlendirmeyi önleyebilir.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Tam typeName.memberName Nitelikli Özellikler  
 *TypeName*. bir öznitelik için *memberName* formu aslında sadece yönlendirilen olay durumda daha evrensel çalışır. Ama diğer durumlarda bu form gereksiz ve bunu önlemek gerekir, sadece biçimlendirme tarzı ve okunabilirlik nedenlerle. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> öznitelik için üç başvuruher tamamen eşdeğerdir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`çünkü bu özellik için nitelikli <xref:System.Windows.Controls.Button> arama başarılı<xref:System.Windows.Controls.Control.Background%2A> (Denetim devralındı) <xref:System.Windows.Controls.Button> ve nesne öğesi veya bir taban sınıf sınıfıdır. `Control.Background`<xref:System.Windows.Controls.Control> sınıf aslında tanımlar <xref:System.Windows.Controls.Control.Background%2A> ve <xref:System.Windows.Controls.Control> bir <xref:System.Windows.Controls.Button> taban sınıf olduğu için çalışır.  
  
 Ancak, aşağıdaki *typeName*. *memberName* formu örneği çalışmıyor ve böylece yorum gösterilir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>başka bir türetilmiş sınıftır <xref:System.Windows.Controls.Control> `Label.Background` ve <xref:System.Windows.Controls.Label> bir nesne öğesi içinde belirtmiş olsaydı, bu kullanım çalışmış olurdu. Ancak, <xref:System.Windows.Controls.Label> sınıf veya taban sınıf <xref:System.Windows.Controls.Button>olmadığı için, belirtilen XAML işlemci `Label.Background` davranışı daha sonra ekli bir özellik olarak işlemektir. `Label.Background`kullanılabilir bir özellik değildir ve bu kullanım başarısız olur.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName Özellik Öğeleri  
 Benzer bir şekilde nasıl *typeName*. *memberName* formu öznitelik sözdizimi, bir *baseTypeName*için çalışır. *üyeAd* sözdizimi özellik öğesi sözdizimi için çalışır. Örneğin, aşağıdaki sözdizimi çalışır:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Burada, özellik öğesi' `Control.Background` nde `Button`yer alsa bile özellik öğesi verilmiştir.  
  
 Ama sadece *typeName*gibi . *öznitelikler* için üyeAdı formu, *baseTypeName*. *memberName* biçimlendirme de kötü bir stildir ve bundan kaçınmalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [XAML Ad Alanı (x:) Dil Özellikleri](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [WPF XAML Uzantıları](wpf-xaml-extensions.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [TypeConverters ve XAML](typeconverters-and-xaml.md)
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
