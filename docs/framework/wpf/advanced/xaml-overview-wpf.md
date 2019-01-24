---
title: XAML genel bakış (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
ms.openlocfilehash: 784dcb88e92169ff8698234e59899cc4d58dd52c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563762"
---
# <a name="xaml-overview-wpf"></a>XAML genel bakış (WPF)
Bu konu XAML dilinin özelliklerini açıklar ve yazmak için XAML nasıl kullanabileceğinizi gösteren [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Bu konu özel olarak uygulandığı şekilde XAML tanımlayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XAML kendisini olan daha büyük bir dil kavramını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>XAML nedir?  
 XAML bir bildirim temelli bir biçimlendirme dilidir. .NET Framework programlama modeli için uygulanan gibi XAML oluşturma basitleştiren bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .NET Framework uygulaması. Oluşturabileceğiniz görünür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerini tanımlayıcı XAML biçimlendirmede ve ardından ayrı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] arka plan kod dosyalarını kullanarak çalışma zamanı mantığını tanımından katılmış kısmi sınıf tanımları aracılığıyla biçimlendirmeye. XAML doğrudan nesneleri belirli bir derlemede tanımlanan türlerin yedekleme kümesi örneğinin temsil eder. Bu, genellikle bir yedekleme türü sistemine doğrudan KRAVAT olmadan yorumlanan bir dil olan çoğu diğer biçimlendirme diller, benzemez. Burada ayrı taraflar çalışabilir üzerinde bir iş akışı XAML sağlayan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve büyük olasılıkla farklı araçlar kullanarak, bir uygulama mantığı.  
  
 Metin olarak temsil edilen zaman XAML dosyaları genellikle sahip XML dosyalarıdır `.xaml` uzantısı. Dosya kodlama, ancak UTF-8 tipik olarak kodlama, XML tarafından kodlanabilir.  
  
 Aşağıdaki örnek, bir düğme parçası olarak nasıl oluşturacağınız gösterir. bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Bu örnekte yalnızca bir özellik nasıl XAML ortak temsil sağlamak üzere tasarlanmıştır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] programlama metaphors (değildir eksiksiz bir örnek).  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Kısaca XAML sözdizimi  
 Aşağıdaki bölümlerde, temel tür XAML sözdizimi açıklayan ve kısa biçimlendirme örneği sağlar. Bu bölümlerde, bu yedekleme türü sistemde nasıl temsil edildiğini gibi her söz dizimi biçimi hakkında tam bilgi sağlamak için amaçlanmamıştır. Daha fazla XAML sözdizimi hakkında bilgi için ayrıntıları her biri bu konu başlığı altında tanıtılan sözdizimi için bkz [içinde XAML söz dizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Birkaç bir sonraki bölüme malzemeleri çoğunu önceki XML dil bilgisi varsa size temel olacaktır. XAML temel tasarım ilkelerinden birini bir sonucu budur.  XAML dil kavramları kendi tanımlar, ancak bu kavramlar XML dil ve biçimlendirme formun içinde çalışır.  
  
### <a name="xaml-object-elements"></a>XAML nesne öğeleri  
 Bir nesne öğesi, genellikle bir türün örneğini bildirir. Bu tür, XAML dili olarak kullanan bir teknoloji için Yedekleme türleri sağlayan derlemelerde tanımlanır.  
  
 Nesne öğesi sözdizimi, her zaman bir açılı ayraç ile başlar (\<). Bu tür adıyla bir örneğini oluşturmak istediğiniz takip eder. (Adın büyük olasılıkla bir ön ek, daha sonra açıklanacaktır bir kavram içerebilir.) Bundan sonra isteğe bağlı olarak öznitelikleri üzerinde nesne öğesi bildirebilirsiniz. Nesne öğesi etiketi tamamlamak için bir kapanış açılı ayraç (>) ile bitmelidir. Bunun yerine, herhangi bir içerik eğik çizgiyle etiket tamamlanıyor ve kapanış açılı ayracı art arda sahip olmayan bir kendi kendine kapanan form kullanabilirsiniz (/ >). Örneğin, daha önce gösterilen biçimlendirme kod parçacığı yeniden bakın:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Bu iki nesne öğeleri belirtir: `<StackPanel>` (içerik ve daha sonra bir kapatma etiketi) ile ve `<Button .../>` (kendi kendine kapanan formu, birkaç öznitelik ile). Nesne öğeleri `StackPanel` ve `Button` her eşlemesi tarafından tanımlanan bir sınıf adını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parçası [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler. Bir nesne öğesi etiketi belirttiğinizde, yeni bir örneğini oluşturmak için işleme XAML için bir yönerge oluşturur. Her örneği, ayrıştırma ve XAML yüklenirken temel türün varsayılan oluşturucusunu çağırarak oluşturulur.  
  
### <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (Özellikler)  
 Bir nesnenin özelliklerini genellikle nesne öğenin öznitelikleri ifade edilebilir. Öznitelik sözdizimi, atama işleci (=) ve ardından özniteliği sözdiziminde ayarlanan özelliğin adı. Bir özniteliğin değeri tırnak işaretleri içinde yer alan bir dize olarak her zaman belirtildi.  
  
 Öznitelik sözdizimi en kolaylaştırılmış özelliği ayarı söz dizimi ve biçimlendirme diller geçmişte kullandığınız geliştiriciler için kullanımı en kolay sözdizimi aşağıdaki gibidir. Örneğin, aşağıdaki biçimlendirme metin kırmızı ve mavi bir arka plan görüntü metni olarak belirtilen ek olarak bulunan bir düğme oluşturur `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Özellik öğesi sözdizimi  
 Nesne veya özellik değeri sağlamak gerekli bilgileri yeterince öznitelik sözdizimi, dize kısıtlamaları ve tırnak işareti içinde ifade olamaz çünkü için bazı özellikleri bir nesne öğesi, öznitelik sözdizimi mümkün değil. Bu durumlarda, özellik öğesi sözdizimine bilinen farklı bir sözdizimi kullanılabilir.  
  
 Özellik öğenin başlangıç etiketinde sözdizimi `<` *typeName*`.`*propertyName*`>`. Genellikle, bu özelliğin değeri olarak alan türü bir nesne öğesi içeriktir. İçerik belirttikten sonra özellik öğesi ile bir bitiş etiketi kapatmanız gerekir. Bitiş etiketi sözdizimi `</` *typeName*`.`*propertyName*`>`.  
  
 Öznitelik sözdizimi mümkündür, öznitelik sözdizimi kullanarak genellikle daha kolay ve daha küçük bir biçimlendirme sağlar, ancak genellikle adımlarından stili, teknik bir sınırlama olan. Aşağıdaki örnek, önceki öznitelik sözdizimi örneği, ancak bu kez olduğu gibi tüm özellikleri için özellik öğesi sözdizimini kullanarak ayarlanan aynı özellikleri gösterir. `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Koleksiyon söz dizimi  
 XAML dil daha okunabilir biçimlendirme oluşturan bazı iyileştirmeler içerir. Belirli bir özellik bir koleksiyon türü, ardından biçimlendirme içinde alt öğeleri bu özelliğin değeri haline koleksiyonunun parçası olarak bildirdiğiniz öğeleri uzun sürerse bir iyileştirme olmasıdır. Bu durumda alt nesne öğelerinin bir koleksiyonunu koleksiyon özelliği için ayarlanan değerdir.  
  
 Aşağıdaki örnek, değerlerini ayarlamak için koleksiyon söz dizimini gösterir. <xref:System.Windows.Media.GradientBrush.GradientStops%2A> özelliği:  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### <a name="xaml-content-properties"></a>XAML İçerik özellikleri  
 XAML ile bir sınıf özelliklerini XAML içerik özelliği tam olarak birine atayabilirsiniz bir dil özelliği belirtir. Bu nesne öğenin alt öğeleri, bu içerik özelliğinin değerini ayarlamak için kullanılır. Diğer bir deyişle, içerik özelliği için benzersiz olarak, XAML biçimlendirme içinde bu özelliği ayarlanırken bir özellik öğesi çıkarın ve daha görünür bir üst/alt benzetme biçimlendirmede üretmek.  
  
 Örneğin, <xref:System.Windows.Controls.Border> bir içerik özelliğine belirtir <xref:System.Windows.Controls.Decorator.Child%2A>. Aşağıdaki iki <xref:System.Windows.Controls.Border> öğeleri aynı şekilde edilir. İlk içerik özelliği söz dizimi avantajlarından yararlanır ve atlar `Border.Child` özellik öğesi. İkincisi gösterir `Border.Child` açıkça.  
  
```xaml  
<Border>  
  <TextBox Width="300"/>  
</Border>  
<!--explicit equivalent-->  
<Border>  
  <Border.Child>  
    <TextBox Width="300"/>  
  </Border.Child>  
</Border>  
```  
  
 XAML dil bir kural olarak, bir XAML İçerik özelliğinin değerini tamamen önce ya da herhangi bir özellik öğe tamamen sonra söz konusu nesne öğesi üzerinde verilmelidir. Örneğin, aşağıdaki biçimlendirme için derlenmiyor:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 XAML İçerik özellikleri bu kısıtlama hakkında daha fazla bilgi için bkz: "XAML İçerik Özellikler" bölümünü [içinde XAML söz dizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Metin içeriği  
 XAML öğeleri az sayıda, doğrudan metin içeriklerini işleyebilir. Bunu etkinleştirmek için aşağıdaki durumlardan biri true olması gerekir:  
  
-   Sınıfı bir içerik özelliğinin bildirmeniz gerekir ve bu içerik özelliği bir dizeye atanabilir bir tür olması gerekir (türü olabilir <xref:System.Object>). Örneğin, herhangi <xref:System.Windows.Controls.ContentControl> kullanan <xref:System.Windows.Controls.ContentControl.Content%2A> içerik özelliği ve bunu türüdür <xref:System.Object>, ve bunu aşağıdaki kullanımı bir pratik üzerinde destekler <xref:System.Windows.Controls.ContentControl> gibi bir <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
-   Türü bir tür dönüştürücüsü metin içeriği çalışması için bu tür dönüştürücüsü başlatma metin olarak kullanılır, bildirmeniz gerekir. Örneğin: `<Brush>Blue</Brush>` Bu uygulamada daha az karşılaşılan bir durumdur.  
  
-   Bilinen bir XAML dil temel türü olmalıdır.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>Birleşik içerik özellikleri ve koleksiyon söz dizimi  
 Bu örneği göz önünde bulundurun:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 Burada, her <xref:System.Windows.Controls.Button> bir alt öğesidir <xref:System.Windows.Controls.StackPanel>. İki farklı nedenlerden iki etiket atlar kolay ve sezgisel bir biçimlendirme budur.  
  
-   **Atlanmış StackPanel.Children özellik öğesi:** <xref:System.Windows.Controls.StackPanel> türetildiği <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel> tanımlar <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> , XAML içerik özelliği.  
  
-   **Atlanmış UIElementCollection nesne öğesi:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> Özelliği türü alır <xref:System.Windows.Controls.UIElementCollection>, uygulayan <xref:System.Collections.IList>. Koleksiyonlar gibi işleme için XAML kurallarına göre koleksiyonunun öğesi etiketi atlanabilir <xref:System.Collections.IList>. (Bu durumda, <xref:System.Windows.Controls.UIElementCollection> çünkü varsayılan bir oluşturucu oluşturmaz ve İşte bu gerçekten oluşturulamaz <xref:System.Windows.Controls.UIElementCollection> nesne öğesi kullanıma açıklamalı gösterilmiştir).  
  
```xaml  
<StackPanel>  
  <StackPanel.Children>  
    <!--<UIElementCollection>-->  
    <Button>First Button</Button>  
    <Button>Second Button</Button>  
    <!--</UIElementCollection>-->  
  </StackPanel.Children>  
</StackPanel>  
```  
  
### <a name="attribute-syntax-events"></a>Öznitelik sözdizimi (olaylar)  
 Öznitelik sözdizimi özellikleri yerine olayları olan üyeler için de kullanılabilir. Bu durumda, özniteliğin adı olay adıdır. WPF uygulamasında olaylar XAML için özniteliğin değeri, bu olayın temsilci uygulayan bir işleyici adıdır. Örneğin, aşağıdaki biçimlendirme için bir işleyici atar <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayına bir <xref:System.Windows.Controls.Button> biçimlendirme içinde oluşturulan:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Daha fazla olayları ve WPF XAML için yeni öznitelik sözdizimi Bu örnek vardır. Örneğin, hangi merak ediyor `ClickHandler` burada temsil eder ve nasıl tanımlandığını başvurulan. Bu yakında açıklanacaktır [olayları ve XAML gerideki kod](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind) bu konudaki.  
  
<a name="case_and_white space_in_xaml"></a>   
## <a name="case-and-white-space-in-xaml"></a>Durum ve XAML boşluk  
 XAML genel olarak bakıldığında büyük/küçük harfe duyarlıdır. Yedekleme türleri çözme amacıyla, WPF XAML CLR büyük küçük harfe duyarlı olduğunu kurallarıyla büyük küçük harfe duyarlı. Nesne öğeleri, özellik öğe ve öznitelik adları tüm derlemesindeki temel alınan türü veya bir tür üyesi adı ile karşılaştırıldığında önemli büyük/küçük harf kullanılarak belirtilmelidir. XAML dil anahtar sözcükleri ve temelleri ayrıca büyük küçük harfe duyarlı değildir. Değerler her zaman büyük/küçük harfe duyarlı değildir. Değerleri büyük/küçük harfe duyarlılık değeri ya da özellik değeri türü alan özellikle ilişkili tür dönüştürücü davranışına bağlı olacaktır. Örneğin, alan özellikleri <xref:System.Boolean> türü ya da alabilir `true` veya `True` ancak çünkü dizeye dönüştürme yerel WPF XAML ayrıştırıcı türü yalnızca eşdeğeri değer olarak <xref:System.Boolean> eşdeğerleri olarak zaten izin verir.  
  
 WPF XAML işlemcisi ve seri hale getiricileri genişletme Yoksay veya tüm önemli olmayan boşluk bırakma ve tüm önemli boşluk Normalleştir. Bu XAML belirtiminde varsayılan boşluk davranışını önerileri ile tutarlıdır. Bu genellikle, davranıştır, XAML İçerik özellikleri içinde dizeleri belirttiğinizde sonucu. En basit terimle, XAML alanları boşluk, satır besleme ve sekme karakterlerinden dönüştürür ve ardından bir boşluk, korur, bitişik dize ya da sonunda bulunamadı. Bu konudaki XAML boşluk işleme ilişkin tam açıklama kapsamında değildir. Ayrıntılar için bkz [XAML içinde işleme boşluk](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Biçimlendirme uzantıları  
 Biçimlendirme uzantıları, XAML dili kavramdır. Bir öznitelik sözdizimi, küme ayracı değeri sağlamak için kullanıldığında (`{` ve `}`) biçimlendirme uzantısı kullanımı gösterir. Bu kullanım öznitelik değerleri genel işleme bir, dize veya dize dönüştürülebilir bir değer olarak erişmek için işleme XAML yönlendirir.  
  
 İçinde kullanılan en yaygın biçimlendirme uzantıları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlama olan [bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), veri bağlama ifadeleri ve kaynak başvuruları için kullanılan [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) ve [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Biçimlendirme uzantıları kullanarak, bu özelliği bir öznitelik söz dizimi genel olarak desteklemiyor olsa bile özellikleri değerlerini sağlamak için öznitelik sözdizimini kullanabilirsiniz. Biçimlendirme uzantıları, ara ifade türleri genellikle değerleri erteleniyor veya yalnızca çalışma zamanında mevcut olan diğer nesnelere başvurma gibi özellikleri etkinleştirmek için kullanın.  
  
 Örneğin, aşağıdaki biçimlendirme değerini ayarlar <xref:System.Windows.FrameworkElement.Style%2A> öznitelik sözdizimi kullanan özellik. <xref:System.Windows.FrameworkElement.Style%2A> Özelliği bir örneğini alır <xref:System.Windows.Style> varsayılan olarak bir öznitelik söz dizimi dizesiyle örneklenemedi sınıfı. Ancak bu durumda, öznitelik bir belirli işaretleme uzantısı başvuruları [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Bu işaretleme uzantısı işlenirken, daha önce bir kaynak sözlüğünde anahtarlı bir kaynak olarak örneklenmiş bir stil bir başvuru döndürür.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Özellikle WPF'de XAML uygulanan için bir başvuru tüm biçimlendirme uzantılarını listelemek için bkz: [WPF XAML uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md). System.Xaml ve .NET Framework XAML uygulamaları için daha yaygın olarak kullanılabilir tarafından tanımlanan biçimlendirme uzantıları başvuru listesi için bkz. [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Biçimlendirme uzantısı kavramları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Tür dönüştürücüleri  
 İçinde [XAML söz dizimi kısaca](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief) bölümünde, öznitelik değeri bir dize tarafından ayarlanabilir belirtilmiştir. Diğer nesne türleri veya İlkel değer dizeleri nasıl dönüştürülür, temel, yerel işleme dayalı <xref:System.String> kendisini yazın, ayrıca yerel bazı işleme türleri gibi <xref:System.DateTime> veya <xref:System.Uri>. Ancak birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türleri ya da bu türlerin üyelerini genişletmek davranışı, daha karmaşık nesne türlerini örneklerini dizeleri ve öznitelikleri belirtilebilir şekilde işlemeyi temel dize özniteliği.  
  
 <xref:System.Windows.Thickness> Yapısı için XAML kullanımları etkin bir tür dönüştürmesi olan bir türü bir örnektir. <xref:System.Windows.Thickness> iç içe geçmiş bir dikdörtgen içindeki ölçüleri gösterir ve değeri olarak gibi özellikler için kullanılan <xref:System.Windows.FrameworkElement.Margin%2A>. Bir tür dönüştürücüsü yerleştirerek tarafından <xref:System.Windows.Thickness>, kullanan tüm özellikleri bir <xref:System.Windows.Thickness> öznitelik olarak belirtilen XAML içinde belirtmeniz daha kolaydır. Aşağıdaki örnek, bir değer sağlamak için bir tür dönüştürme ve öznitelik sözdizimi kullanır. bir <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 Önceki öznitelik sözdizimi örneği aşağıdakine eşdeğerdir daha ayrıntılı sözdizimi örneği burada <xref:System.Windows.FrameworkElement.Margin%2A> bunun yerine özellik öğesi sözdizimi içeren aracılığıyla ayarlanan bir <xref:System.Windows.Thickness> nesne öğesi. Dört anahtar özelliklerini <xref:System.Windows.Thickness> öznitelik olarak yeni örnek üzerinde ayarlanır:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Sınırlı sayıda tür dönüştürme türü varsayılan bir oluşturucuya sahip olmadığı için özellik bu tür için bir alt karıştırılmaksızın ayarlamak için tek genel yol olduğu nesnelerin vardır. <xref:System.Windows.Input.Cursor> bunun bir örneğidir.  
  
 Söz dizimi desteklenir tür dönüştürme ve uygunsa kullanımını nasıl özniteliği hakkında daha fazla bilgi için bkz: [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML kök öğe ve XAML ad alanları  
 Bir XAML dosyası her iki bir doğru biçimlendirilmemiş için yalnızca bir kök öğe olmalıdır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosya ve geçerli bir XAML dosyası. WPF uygulama modeli tanınmış bir anlamı bir kök öğe kullandığınız tipik WPF senaryoları için (örneğin, <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> bir sayfa için <xref:System.Windows.ResourceDictionary> için dış bir sözlük veya <xref:System.Windows.Application> uygulama tanımı için). Aşağıdaki örnek, kök öğesi için tipik bir XAML dosyasını gösterir. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasıyla kök öğesi <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Kök öğe özniteliklerini de içeren `xmlns` ve `xmlns:x`. Bu öznitelikler için XAML ad alanları, yedekleme öğeleri olarak işaretleme Bakacağınız türler için tür tanımları içeren bir XAML işlemcisi belirtin. `xmlns` Öznitelik özellikle varsayılan XAML ad alanı gösterir. Varsayılan XAML ad alanı içinde bir ön eki nesne öğeleri biçimlendirmede belirtilebilir. Çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama senaryoları ve neredeyse tüm verilen örneklerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölümlerini [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], varsayılan XAML ad alanı için eşlenmiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ad alanı [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. `xmlns:x` XAML dil ad alanı eşleyen bir ek XAML ad alanı özniteliği gösterir [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 Bu kullanımı `xmlns` kullanımı ve bir namescope eşlemesi için bir kapsam tanımlamak için XML 1.0 belirtimi ile tutarlıdır. Yalnızca XAML namescope ayrıca tür çözümlemesi ve XAML ayrıştırma geldiğinde namescope'nın öğe türlerine göre nasıl yedeklenir ilgili bir sorun olduğu anlamına gelir, XAML ad kapsamları XML ad kapsamları farklıdır.  
  
 Unutmayın `xmlns` öznitelikleri her XAML dosyasının kök öğede duyulandan yalnızca. `xmlns` tanımlamalar kök öğenin tüm alt öğeleri için geçerlidir (Bu davranışı için XML 1.0 belirtimi ile yeniden tutarlıdır `xmlns`.) `xmlns` öznitelikler de diğer öğeleri kök altında izin verilir ve tanımlama öğenin tüm alt öğelerine uygulanacak. Ancak, sık sık tanımı veya XAML ad alanları yeniden tanımlama okunması zor olan bir XAML biçimlendirme stili neden olabilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] WPF core derleme tanıma sahip bir altyapı XAML işlemcisinin uygulaması içerir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Destekleyen türleri içeren için çekirdek derlemeler bilinir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan XAML ad alanı eşlemeleri. Bu proje yapınızın bir parçası olan yapılandırma etkin dosya ve WPF, yapı ve proje sistemleri. Bu nedenle, varsayılan olarak varsayılan XAML ad alanı bildirme `xmlns` gelen XAML öğeleri başvurmak için gerekli olan tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler.  
  
### <a name="the-x-prefix"></a>X: ön eki  
 Önceki örnekte kök öğesi, ön eki `x:` XAML ad alanı eşlemek için kullanılan [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], XAML dili destekleyen özel XAML ad alanı olan oluşturur. Bu `x:` ön eki bu XAML ad alanı için proje şablonları, örnekler ve belge boyunca bu eşleme için kullanılan [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. XAML dili için XAML ad alanı, XAML içinde çok sık kullanacağınız çeşitli programlama yapıları içerir. En yaygın bir listesi verilmiştir `x:` kullanacağınız programlama yapıları öneki:  
  
-   [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md): Her kaynak için benzersiz bir anahtar ayarlar bir <xref:System.Windows.ResourceDictionary> (veya diğer çerçeveler benzer sözlük kavramları). `x:Key` % 90'ını hesabı görür `x:` kullanımları bir tipik WPF uygulama biçimlendirme içinde görürsünüz.  
  
-   [x: Class](../../../../docs/framework/xaml-services/x-class-directive.md): Belirtir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanını ve sınıf adı için bir XAML sayfası için arka plan kod sağlayan sınıf. Arka plan kod WPF programlama modeli başına desteklemek için sınıf olması ve bu nedenle, neredeyse her zaman görmek `x:` kaynak olsa bile, eşlenmiş.  
  
-   [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md): Bir nesne öğesi işlendikten sonra var olan bir örneği için bir çalışma zamanı nesne adı, çalışma zamanı kodu belirtir. Genel olarak, bir WPF tanımlı eşdeğer özelliği sık kullanacağınız [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Gibi özellikleri özelliği yedekleyen bir CLR özel eşleme ve bu nedenle, sık sık çalışma zamanında kodu başlatılmış XAML adlandırılmış öğeleri bulmak için kullandığınız uygulama programlaması için daha kolay. En yaygın tür özelliği <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Yine de kullanabilir [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) olduğunda eşdeğer WPF çerçeve düzeyi <xref:System.Windows.FrameworkElement.Name%2A> özelliği, belirli bir türü desteklenmiyor. Bu, bazı animasyon senaryolarda oluşur.  
  
-   [x: Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): Aksi takdirde bir XAML uyumlu özelliği değil statik bir değer döndüren bir başvuru sağlar.  
  
-   [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): Oluşturur bir <xref:System.Type> başvuru bir tür adına bağlı. Bu öznitelikler belirtmek için kullanılan <xref:System.Type>, gibi <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, sık özelliği yerel dize olsa-için-<xref:System.Type> şekilde dönüştürme, [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) biçimlendirme uzantısı kullanımı İsteğe bağlı.  
  
 Vardır yapılardan programlama ek `x:` gibi ortak olmayan ön eki/XAML ad alanı. Ayrıntılar için bkz [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Özel ön ekleri ve XAML özel türleri  
 Kendi özel derlemeler için ya da WPF çekirdek PresentationCore, PresentationFramework ve WindowsBase dışında derlemeler için derleme özel bir parçası olarak belirtebilirsiniz `xmlns` eşleme. Bu tür çalışıyorsunuz. XAML kullanımları desteklemek için doğru bir şekilde uygulandığından sürece, XAML içinde bu derleme türleri ardından başvurabilirsiniz.  
  
 XAML biçimlendirmede nasıl özel önekleri çalışmanın çok basit bir örneği verilmiştir. Önek `custom` kök öğe etiketinde tanımlanır ve paketlenmiş ve uygulama ile birlikte kullanılabilir olduğu belirli bir derleme eşlenir. Bu derlemeyi bir tür içeren `NumericUpDown`, genel XAML kullanım yanı sıra bir WPF XAML içerik modelinde belirli bu noktada, ekleme izin veren bir sınıf devralma kullanarak desteklemek için uygulanır. Bu örneği `NumericUpDown` denetimi, bir nesne öğesi olarak bildirilir, XAML ayrıştırıcı hangi XAML bilebilmesi önekini kullanarak ad alanı türü içerir ve bu nedenle burada yedekleme derleme, tür tanımını içeren.  
  
```  
<Page  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"  
    >  
  <StackPanel Name="LayoutRoot">  
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>  
...  
  </StackPanel>  
</Page>  
```  
  
 XAML özel türleri hakkında daha fazla bilgi için bkz: [XAML ve özel sınıflar için WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
 XML ad alanları ve ad alanlarını derlemelerde yedekleme kodunun nasıl ilişkili olduğunu hakkında daha fazla bilgi için bkz. [XAML ad alanları ve WPF XAML Namespace eşleme](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Olayları ve XAML kodu arka plan  
 Çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları hem XAML biçimlendirme ve arka plan kod oluşur. Bir proje içinde XAML olarak yazılmış bir `.xaml` dosyası ve bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dil Microsoft Visual Basic veya C# gibi bir arka plan kod dosyası yazmak için kullanılır. Bir XAML dosyası WPF programlama ve uygulama modelleri bir parçası olarak biçimlendirme derlenirken, XAML kodu arka plan konumunu bir XAML dosyasını bir ad belirterek tanımlanan dosya ve sınıf olarak `x:Class` XAML kök öğesinin özniteliği.  
  
 Örneklerde şu ana kadar çeşitli düğmeler gördünüz, ancak bu düğmeler hiçbiri henüz ilişkili herhangi bir mantıksal davranış vardı. Bir nesne öğesi için bir davranış eklemek için birincil uygulama düzeyinde öğe sınıfın var olan bir olayı kullanın ve çalışma zamanında bu olay ortaya çıktığında çağrılan bu olay için belirli bir işleyici yazılacak mekanizmadır. İşleyicinizi uygulayan kod, arka plan kod içinde tanımlanır ancak olay adını ve kullanılacak işleyicisi adı biçimlendirme içinde belirtilir.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Arka plan kod dosyası CLR ad alanını kullandığından emin olun `ExampleNamespace` ve bildirir `ExamplePage` olarak bu ad alanı içinde kısmi bir sınıf. Bu parallels `x:Class` öznitelik değerini `ExampleNamespace`.`ExamplePage` Bu işaretleme kök dizininde sağlanmadı. Kök öğesi türünden bir sınıf türetilerek WPF biçimlendirmesi derleyici herhangi derlenmiş XAML dosyası için bir parçalı sınıf oluşturun. Ayrıca aynı kısmi sınıf tanımlar gerideki sağladığınızda, sonuç kodunu aynı ad alanını ve sınıf derlenmiş uygulamanın içinde birleştirilir.  
  
 Arka plan kod programlama ' WPF'de gereksinimleri hakkında daha fazla bilgi için "arka plan kod, olay işleyicisi ve kısmi sınıf gereksinimleri" bölümüne bakın. [arka plan kod ve WPF XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
 Ayrı arka plan kod dosyası oluşturmak istemiyorsanız, satır içi kodunuzu bir XAML dosyasında da kullanabilirsiniz. Ancak, önemli sınırlamalar daha az verimli bir yöntem satır içi kodudur. Ayrıntılar için bkz [arka plan kod ve WPF XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Yönlendirilmiş olaylar  
 Belirli bir olay özelliği için temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş bir olaydır. Olayları etkinleştir öğeleri arasında ağacı ilişki bağlı olduğu sürece farklı bir öğe tarafından başlatılan bir olayı işlemek için bir öğe yönlendirilir. Olay işleme XAML özniteliği ile belirtirken, yönlendirilmiş olay için dinledik ve bu belirli olay sınıfı üyeleri tablosunda listelemez öğeleri dahil olmak üzere herhangi bir öğedeki işlenmiş. Bu olay ad özniteliği, sahip olan sınıf adıyla uygun olarak gerçekleştirilir. Örneğin, üst `StackPanel` sürekli olarak `StackPanel`  /  `Button` örnek bir alt öğe düğmenin işleyicisi kaydetmek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öznitelik belirterek olay `Button.Click` üzerinde `StackPanel` öznitelik değeri olarak işleyici adınızla nesne öğesi. Nasıl yönlendirilmiş olaylar çalışma hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>XAML öğeleri adlı  
 Varsayılan olarak, benzersiz bir kimlik veya nesne başvurusu bir nesne grafında XAML nesne öğesi işleme tarafından oluşturulan nesne örneği sahip değil. Kod Oluşturucusunu, örnek daha sonra kodunuzda başvurabilir, böylece buna karşılık, neredeyse her zaman Oluşturucu sonuç için oluşturulan örnek, bir değişken ayarlamak için kullanın. XAML işaretleme tanımıyla oluşturulan nesneler için standartlaştırılmış bir erişim sağlamak için tanımlar [x: Name özniteliği](../../../../docs/framework/xaml-services/x-name-directive.md). Değerini ayarlayabilirsiniz `x:Name` herhangi bir nesne öğesi özniteliği. Arka plan kod içinde seçtiğiniz tanımlayıcısı için oluşturulan örnek başvuran bir örnek değişkeni eşdeğerdir. Tüm açılardan nesne örnekleri (adı, bu örneğe başvuran) olmadıklarını ve adlandırılmış öğeleri çalışma zamanı etkileşimleri uygulama içinde işlemek için arka plan kod başvurabilirsiniz yokmuş gibi öğeleri işlevi adı. Örnekleri değişkenleri arasındaki bu bağlantı, WPF XAML biçimlendirme derleyici tarafından gerçekleştirilir ve daha fazla özel özellikler ve desenleri gibi ilgili <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> , açıklanmayan bu konudaki ayrıntılı.  
  
 WPF çerçeve düzeyi XAML öğeleri devralınan bir <xref:System.Windows.FrameworkElement.Name%2A> tanımlanan XAML eşdeğer olan özellik `x:Name` özniteliği. Belirli diğer sınıflar için özellik düzeyi eşdeğerleri de sağlar. `x:Name`, ayrıca genel olarak tanımlanan olarak bir `Name` özelliği. Bulamazsanız, genellikle, konuşma bir `Name` seçilen öğe/türünüzü kullanmak için Üyeler tablosunda özelliğinde `x:Name` yerine. `x:Name` Değerleri çalışma zamanında belirli alt sistemler veya yardımcı program yöntemleri gibi kullanılabilecek bir XAML öğesi için bir tanımlayıcı sağlar <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.FrameworkElement.Name%2A> üzerinde bir <xref:System.Windows.Controls.StackPanel> öğesi. Ardından, bir işleyici bir <xref:System.Windows.Controls.Button> içindeki <xref:System.Windows.Controls.StackPanel> başvuruları <xref:System.Windows.Controls.StackPanel> kendi örneği başvuru aracılığıyla `buttonContainer` tarafından ayarlanmış <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Böylece adları, tahmin edilebilir olan belirli bir kapsama içinde benzersiz olması zorunlu tutulabilir bir değişken gibi yalnızca bir örneği için XAML ad kapsamı, bir kavramı tarafından yönetilir. Bir sayfa tanımlayan birincil biçimlendirme XAML namescope sınır o sayfanın kök öğe olan benzersiz bir XAML namescope gösterir. Ancak, diğer biçimlendirme kaynakları stiller veya şablonlar stiller içinde gibi çalışma zamanında bir sayfa ile etkileşim kurabilir ve biçimlendirme gibi kaynakları, genellikle mutlaka sayfanın XAML namescope ile bağlamayın kendi XAML ad kapsamları sahiptir. Daha fazla bilgi için `x:Name` ve XAML ad kapsamları, <xref:System.Windows.FrameworkElement.Name%2A>, [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md), veya [WPF XAML ad kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Ekli özellikler ve ekli olaylar  
 XAML belirli özellikler veya herhangi bir öğede bir özellik veya olay üzerinde ayarlanmış öğesi türü tanımlarında var olup bağımsız olarak, belirtilen olayları sağlayan bir dil özelliği belirtir. Bu özellik özellikleri sürümünün ekli özelliği adı, olayları sürüm ekli olay çağrılır. Kavramsal olarak, tüm XAML öğesi/Pro instanci objektu ayarlanabilir genel üyeleri olarak ekli özellikler ve ekli olaylar düşünebilirsiniz. Ancak, bu öğe/sınıfı ya da daha büyük bir altyapısı yedekleme özelliği deposu ekli değerlerini desteklemesi gerekir.  
  
 XAML içinde ekli özellikler genellikle öznitelik söz dizimi aracılığıyla kullanılır. Nitelik söz dizimindeki ekli özelliği biçiminde belirtin *ownerType*. *propertyName*.  
  
 Yüzeysel olarak, bu özellik öğesi kullanımı benzer, ancak bu durumda *ownerType* belirtin, her zaman farklı bir nesne öğesi tür ekli özellik nerede ayarlanır. *ownerType* ekli özellik değerini alma veya ayarlama yapmak için XAML işlemcisi tarafından gerekli erişimci metotlarını sağlayan tür.  
  
 İliştirilmiş özellikler için en yaygın senaryo için kendi üst öğesi bir özellik değeri bildirmek alt öğeleri etkinleştirmektir.  
  
 Aşağıdaki örnekte gösterilmiştir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özellik. <xref:System.Windows.Controls.DockPanel> Sınıfı tanımlar için erişimciler <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ve bu nedenle ekli özellik. <xref:System.Windows.Controls.DockPanel> Sınıfı da onun alt öğeleri yinelenir ve her öğe için bir değerini özellikle denetler mantığı içerir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Bir değeri bulunamazsa, bu değer alt öğeleri konumlandırmak için Düzen sırasında kullanılır. Kullanım <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özellik konumlandırma bu özelliği olduğundan, aslında motive edici temel senaryo için <xref:System.Windows.Controls.DockPanel> sınıfı.  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], çoğu veya tamamı iliştirilmiş özellikler de bağımlılık özellikleri uygulanır. Ayrıntılar için bkz [ekli özelliklere genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Ekli olaylar kullanmak benzer *ownerType*. *eventName* öznitelik söz dizimi biçimi. Yalnızca bağlı olmayan olaylar gibi öznitelik değeri XAML içinde ekli bir olay için olay öğede ele alındığında çağrılan işleyici yönteminin adı belirtir. WPF XAML içinde ekli olay kullanımları daha az yaygındır. Daha fazla bilgi için [iliştirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Taban türleri ve XAML  
 Temel alınan WPF XAML ve XAML ad alanı, karşılık gelen türler koleksiyonudur [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesnelerin XAML için işaretleme öğeleri yanı sıra. Ancak, tüm sınıflar öğelerine eşlenebilir. Soyut sınıflar, gibi <xref:System.Windows.Controls.Primitives.ButtonBase>, ve belirli soyut olmayan temel sınıflar devralma için kullanılan [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne modeli. Üyeleri somut XAML öğelerin her biri, hiyerarşideki bazı temel sınıftan devraldığı için temel sınıf, soyut olanlar da dahil olmak üzere XAML geliştirme için yine de önemlidir. Genellikle bu üyeler öznitelik olarak öğe üzerinde ayarlanabilir özellikleri veya işlenebilir olayları içerir. <xref:System.Windows.FrameworkElement> somut temeli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sınıfının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] WPF framework düzeyinde. Tasarlarken [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]kullanacağınız çeşitli şekli, paneli, dekoratör veya denetim sınıfları, tüm türetilen <xref:System.Windows.FrameworkElement>. İlgili bir temel sınıf <xref:System.Windows.FrameworkContentElement>, iyi bir akış düzeni sunum için belge yönelimli ve iş öğeleri destekler kullanarak [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] kasıtlı olarak yansıtan [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] içinde <xref:System.Windows.FrameworkElement>. Öğe düzeyinde öznitelikler birleşimi ve [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne modeli ile belirli bir XAML öğesini ve kendi temel türü ne olursa olsun en somut XAML öğeleri üzerinde ayarlanabilir ortak özellikler kümesi, sağlar.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML güvenlik  
 XAML doğrudan nesne örneklemesini ve yürütme temsil eden bir biçimlendirme dilidir. Bu nedenle, XAML içinde oluşturulan öğeler aynı oluşturulan eşdeğer olarak ile sistem kaynakları (ağ erişimi, dosya sistemi g/ç örnek) etkileşim olanağı sahip kodu yapar.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] destekleyen [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] güvenlik çerçevesi [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]. Diğer bir deyişle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Internet bölgesinde çalışan içeriği yürütme izinleri azaltıldı. "Kaybetmiş XAML" (derlenmemiş XAML sayfaları yorumlanan yükleme zamanında bir XAML Görüntüleyicisi) ve [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] genellikle bu Internet bölgesinde çalıştırılan ve aynı izin kümesi kullanın.  Ancak, barındırma uygulaması gibi tam olarak güvenilen bir uygulama için yüklenmiş XAML sistem kaynaklarına aynı erişim vardır. Daha fazla bilgi için [WPF kısmi güven güvenliği](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>XAML kodunu yükleniyor  
 XAML UI tüm tanımlamak için kullanılabilir, ancak bazen de yalnızca bir kullanıcı arabirimi XAML içinde tanımlamak uygundur. Bu özellik, bir iş nesnesi ya da olası senaryolar çeşitli XAML kullanarak bilgileri, yerel depolaması olan kısmi özelleştirmeyi etkinleştirmek için kullanılabilir. Bu senaryolar için anahtar <xref:System.Windows.Markup.XamlReader> sınıf ve onun <xref:System.Windows.Markup.XamlReader.Load%2A> yöntemi. Giriş bir XAML dosyası olduğunu ve çıkış, biçimlendirmeden oluşturulan çalışma zamanı nesne ağacının tümünü temsil eden bir nesnedir. Uygulamada zaten başka bir nesnenin bir özellik olarak nesneyi daha sonra ekleyebilirsiniz. Uygun bir içerik modeli nihai görüntüleme yetenekleri olan ve uygulamaya yeni içerik eklendi, yürütme altyapısı bildireceğiz özelliğinde özellik olduğu sürece, çalışan bir uygulamanın içerikleri kolayca değiştirebilirsiniz XAML yükleme tarafından. Bu özellik genellikle yalnızca çalıştırılmakta olan uygulamalara dosyaları yükleme güvenliğe dayalı bariz etkileri nedeniyle tam güven uygulamalarında kullanılabilir olduğunu unutmayın.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Yenilikler  
 WPF ile olduğu gibi bu konuda XAML söz dizimi kavramları ve terminolojiyi temel bir giriş sağlar. Burada kullanılan terimler hakkında daha fazla bilgi için bkz. [içinde XAML söz dizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Zaten bunu yapmadıysanız, öğretici konusundaki alıştırmalar deneyin [izlenecek yol: İlk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Öğretici tarafından tanımlanan biçimlendirme odaklı uygulama oluşturduğunuzda, bu konuda açıklanan kavramlardan bir çoğunu güçlendirmek alıştırma yardımcı olur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel alan belirli uygulama modelini kullanan <xref:System.Windows.Application> sınıfı. Ayrıntılar için bkz [uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
 [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) XAML kapsamlı uygulamaların komut satırından ve ile nasıl yapılandırıldığı hakkında daha fazla ayrıntı sağlar [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) özelliklerinde yönlülük hakkında daha fazla bilgi veren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve bağımlılık özellikleri kavramını sunmaktadır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
- [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML Uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)
- [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
- [WPF İçinde Ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
