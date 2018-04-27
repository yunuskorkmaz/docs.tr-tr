---
title: XAML'ye Genel Bakış (WPF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 57
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 87785d6bba58442a1a5ad27f5304aa63e16c1aa9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="xaml-overview-wpf"></a>XAML'ye Genel Bakış (WPF)
Bu konu, XAML dili özelliklerini açıklar ve yazmak için XAML nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Bu konuda özellikle tarafından uygulanan XAML açıklanmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. XAML kendisini olduğu daha büyük bir dil kavram [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>XAML nedir?  
 XAML bildirim temelli biçimlendirme dilidir. Uygulanan gibi [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] programlama modeli, XAML oluşturma basitleştirir. bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için bir [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama. Oluşturabileceğiniz görünür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri bildirim temelli XAML biçimlendirme ve sonra ayrı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] arka plan kod dosyaları kullanarak çalışma zamanı mantığı tanımından birleştirilmiş parçalı sınıf tanımları aracılığıyla biçimlendirme için. XAML doğrudan belirli bir derlemede tanımlanan türlerin yedekleme kümesi nesneleri örneklemesi temsil eder. Bu, genellikle bir yedekleme türü sistemine doğrudan bağ olmadan yorumlanan bir dil olan çoğu diğer biçimlendirme dil benzemez. XAML etkinleştirir burada ayrı tarafların çalışabilir üzerinde bir iş akışı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve farklı araçlar kullanarak bir uygulama mantığı.  
  
 Metin olarak gösterilen, XAML dosyaları genellikle içeren XML dosyalarıdır `.xaml` uzantısı. Dosya kodlama, ancak UTF-8 tipik olarak kodlama herhangi XML tarafından kodlanmış olması.  
  
 Aşağıdaki örnek, bir düğme parçası olarak nasıl oluşturacağınız gösterir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Bu örnek yalnızca XAML nasıl ortak temsil eder, bir özellik sağlamak üzere tasarlanmıştır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (olmadığı tam bir örnek) metaphors programlama.  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>Kısa XAML sözdizimi  
 Aşağıdaki bölümlerde, temel tür XAML sözdizimi açıklayan ve kısa biçimlendirme örneği verin. Bu bölümler bu yedekleme türü sistemindeki nasıl temsil edildiğini gibi her sözdizimi form hakkında tam bilgi sağlamak üzere tasarlanmamıştır. Daha fazla XAML sözdizimi hakkında bilgi için ayrıntıları her Bu konu başlığı altında tanıtılan sözdizimi için bkz [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Sonraki birkaç bölümlerde malzeme çoğunu XML dili önceki aşina varsa, başlangıç olacaktır. XAML temel tasarım ilkeleri birinin sonucu budur.  XAML dil kavramları kendi tanımlar, ancak bu kavramlar çalışma içinde XML dil ve biçimlendirme formu.  
  
### <a name="xaml-object-elements"></a>XAML nesne öğeleri  
 Object öğesi, genellikle bir türünün bir örneği bildirir. Bu tür, XAML dili olarak kullanan bir teknoloji için Yedekleme türleri sağlayan derlemelerde tanımlanır.  
  
 Nesne öğesi sözdizimi her zaman bir açılı ayraç ile başlar (\<). Bu tür adıyla örnek oluşturmak istediğiniz izler. (Adı büyük olasılıkla bir önek, daha sonra açıklanacaktır bir kavram içerebilir.) Bundan sonra isteğe bağlı olarak öznitelikleri nesnesi öğesinde bildirebilirsiniz. Nesne öğe etiketi tamamlamak için kapanış açılı ayraç (>) bitmelidir. Bunun yerine eğik çizgiyle etiket tamamlama ve kapanış açılı ayracı art arda tarafından herhangi bir içerik yok kendi kendine kapanan bir form kullanabilirsiniz (/ >). Örneğin, daha önce gösterilen işaretleme parçacığı yeniden bakın:  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Bu iki nesne öğeleri belirtir: `<StackPanel>` (ile içerik ve daha sonra bir kapanış etiketi), ve `<Button .../>` (kendi kendine kapanan formu, birkaç öznitelik ile). Nesne öğeleri `StackPanel` ve `Button` tarafından tanımlanan bir sınıf adı için her eşleme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve parçası olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler. Bir nesne öğe etiketinde belirttiğinizde, yeni bir örneğini oluşturmak için işleme XAML için yönerge oluşturun. Her örneği, ayrıştırma ve XAML yükleme temel türün varsayılan oluşturucusunu çağırarak oluşturulur.  
  
### <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (Özellikler)  
 Bir nesnenin özelliklerini genellikle object öğesi özniteliklerini ifade edilebilir. Bir öznitelik sözdizimi atama işleci (=) ve ardından öznitelik sözdiziminde ayarlamak özellik adları. Bir özniteliğin değeri, her zaman tırnak işaretleri içinde yer alan bir dize olarak belirtilir.  
  
 Öznitelik sözdizimi en kolaylaştırılmış özellik ayarı sözdizimi ve biçimlendirme dillerini geçmişte kullanmış geliştiriciler için kullanılacak en sezgisel sözdizimi aşağıdaki gibidir. Örneğin, aşağıdaki biçimlendirme kırmızı metin ve görüntü metni olarak belirtilen yanı sıra mavi bir arka plan sahip bir düğme oluşturur `Content`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Özellik öğesi sözdizimi  
 Nesne veya özellik değeri sağlamak için gerekli olan bilgileri yeterli öznitelik sözdizimi dize kısıtlamalarını ve tırnak işareti içinde açıklanamayan çünkü için bazı özellikleri bir nesne öğenin öznitelik sözdizimi mümkün değil. Bu durumlarda, özellik öğesi sözdizimini bilinen farklı bir sözdizimi kullanılabilir.  
  
 Özellik öğenin başlangıç etiketinde sözdizimi `<` *typeName*`.`*propertyName*`>`. Genellikle, bu etiketi içeriğini bir değer olarak özelliği alır türü nesne öğesidir. İçerik belirttikten sonra bir bitiş etiketi özelliği öğeyle kapatmanız gerekir. Bitiş etiketi sözdizimi `</` *typeName*`.`*propertyName*`>`.  
  
 Bir öznitelik sözdizimi olası ise, öznitelik sözdizimini kullanarak genellikle daha kolaydır ve daha küçük bir işaretleme sağlar, ancak genellikle sağlasa da, yalnızca stili, teknik bir sınırlama değil. Aşağıdaki örnek, önceki öznitelik sözdizimi örneği, ancak bu kez olduğu gibi tüm özellikler için özellik öğesi sözdizimini kullanarak ayarlanan aynı özellikleri gösterir `Button`.  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>Koleksiyon sözdizimi  
 XAML dili daha okunabilir biçimlendirme oluşturan bazı en iyi duruma getirmeleri içerir. Belirli bir özelliği bir koleksiyon türü, sonra alt öğelerin bu özelliğin değeri hale koleksiyonunun bir parçası olarak biçimlendirme bildirin öğeleri uzun sürerse bir iyileştirme olmasıdır. Bu durumda alt nesne öğelerini koleksiyon özelliği için ayarlanan değer koleksiyonudur.  
  
 Aşağıdaki örnekte değerlerini ayarlamak için koleksiyon sözdizimi gösterilmektedir <xref:System.Windows.Media.GradientBrush.GradientStops%2A> özelliği:  
  
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
 XAML bir sınıf özelliklerini XAML içerik özelliği tam olarak birine yapabildiği belirleyebileceğiniz bir dil özelliği belirtir. Bu nesne öğenin alt öğelerinin bu içerik özelliğinin değeri ayarlamak için kullanılır. Diğer bir deyişle, için içerik özelliği benzersiz olarak, bu özellik XAML biçimlendirme ayarlarken bir özellik öğesi atlayın ve biçimlendirme içinde daha görünür bir üst/alt benzetimini üretmek.  
  
 Örneğin, <xref:System.Windows.Controls.Border> içerik özelliğini belirtir <xref:System.Windows.Controls.Decorator.Child%2A>. Aşağıdaki iki <xref:System.Windows.Controls.Border> öğeleri kabul edilir aynı. İlk içerik özelliği sözdizimi avantajlarından yararlanır ve atlar `Border.Child` özellik öğesi. İkincisi gösterir `Border.Child` açıkça.  
  
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
  
 XAML dili kural olarak, XAML İçerik özelliğinin değeri tamamen önce veya tamamen sonra herhangi bir özellik öğe bu nesnenin öğede verilmesi gerekir. Örneğin, aşağıdaki biçimlendirme derlenmiyor:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 XAML İçerik özellikleri bu kısıtlama hakkında daha fazla bilgi için "XAML içeriği Özellikler" bölümüne bakın [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
### <a name="text-content"></a>Metin içeriği  
 XAML öğeleri az sayıda içeriklerini doğrudan metin işleyebilir. Bunu etkinleştirmek için aşağıdaki durumlardan biri doğru olmalıdır:  
  
-   İçerik özelliği sınıfı bildirmeniz gerekir ve bu içerik özelliği bir dize atanabilir bir tür olmalıdır (türü olabilir <xref:System.Object>). Örneğin, herhangi <xref:System.Windows.Controls.ContentControl> kullanan <xref:System.Windows.Controls.ContentControl.Content%2A> içerik özelliği ve onu türüdür <xref:System.Object>, ve bu pratik üzerinde aşağıdaki kullanım destekler <xref:System.Windows.Controls.ContentControl> gibi bir <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
-   Türü tür dönüştürücüsünü metin içeriği çalışması için bu tür dönüştürücüsünü başlatma metni olarak kullanılır, belirtmesi gerekir. Örneğin, `<Brush>Blue</Brush>`. Bu uygulamada daha az görülen bir durumdur.  
  
-   Basit bir bilinen XAML dili türünden olmalıdır.  
  
### <a name="content-properties-and-collection-syntax-combined"></a>İçerik özellikleri ve birleştirilmiş toplama sözdizimi  
 Bu örneği göz önünde bulundurun:  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 Burada, her <xref:System.Windows.Controls.Button> bir alt öğesi olan <xref:System.Windows.Controls.StackPanel>. İki farklı nedenlerle iki etiket atlar kolay ve sezgisel bir işaretleme budur.  
  
-   **Atlanan StackPanel.Children özellik öğesi:** <xref:System.Windows.Controls.StackPanel> türetilen <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel> tanımlar <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> kendi XAML içerik özelliği.  
  
-   **Atlanan UIElementCollection object öğesi:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> özelliği alır türü <xref:System.Windows.Controls.UIElementCollection>, hangi uygular <xref:System.Collections.IList>. Koleksiyonları gibi işlemek için XAML kurallar temel alınarak koleksiyonun öğe etiketi atlanabilir <xref:System.Collections.IList>. (Bu durumda, <xref:System.Windows.Controls.UIElementCollection> gerçekten varsayılan bir oluşturucu kullanıma sunmuyor ve nedeni başlatılamaz <xref:System.Windows.Controls.UIElementCollection> object öğesi çıkışı açıklamalı gösterilmiştir).  
  
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
  
### <a name="attribute-syntax-events"></a>Öznitelik sözdizimi (olay)  
 Öznitelik sözdizimi özellikler yerine olayları olan üyeleri için de kullanılabilir. Bu durumda, özniteliğin adı olay adıdır. WPF uygulamasında olayların XAML özniteliğin değeri, bu olayın temsilci uygulayan bir işleyici adıdır. Örneğin, aşağıdaki biçimlendirme için bir işleyici atar <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaya bir <xref:System.Windows.Controls.Button> biçimlendirmede oluşturuldu:  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 Daha fazla olaylara ve WPF XAML yalnızca öznitelik sözdizimi Bu örnek vardır. Örneğin, size ne merak ediyor `ClickHandler` burada temsil eder ve nasıl tanımlanır başvurulan. Bu yaklaşan açıklanacaktır [olaylar ve XAML arka plan kod](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind) bölümüne.  
  
<a name="case_and_whitespace_in_xaml"></a>   
## <a name="case-and-whitespace-in-xaml"></a>Durum ve XAML'de boşluk  
 XAML genel olarak bakıldığında büyük küçük harfe duyarlıdır. Yedekleme türleri çözümleme, WPF XAML CLR büyük küçük harfe duyarlı olduğunu kurallarıyla büyük küçük harfe duyarlı amaçlıdır. Nesne öğeleri, özellik öğelerinin ve öznitelik adları tüm ad derlemesindeki temel alınan türü ya da bir türünün bir üyesi tarafından karşılaştırıldığında hassas büyük küçük harf kullanılarak belirtilmelidir. XAML dil anahtar sözcükleri ve temelleri ayrıca büyük küçük harfe duyarlı değildir. Değerleri her zaman büyük küçük harfe duyarlı değildir. Değerleri için büyük/küçük harfe duyarlılık değeri ya da özellik değeri türü alan özellik ile ilişkilendirilmiş türü dönüştürücü davranışına bağlı olacaktır. Örneğin, ele özellikleri <xref:System.Boolean> türü ya da alabilir `true` veya `True` ancak yerel WPF XAML ayrıştırıcısı yazın çünkü dizeye dönüştürme eşdeğer değerleri olarak <xref:System.Boolean> zaten eşdeğerleri olarak verir.  
  
 WPF XAML işlemcileri ve serileştiricileri Yoksay veya tüm önemli olmayan boşluk bırakın ve tüm önemli boşluk normalleştirin. XAML belirtimi varsayılan boşluk davranışı önerileri tutarlı budur. Bu genellikle bir davranıştır XAML İçerik özellikleri içindeki dizeleri belirttiğinizde sonucu olarak. En basit terimleriyle XAML alan, satır besleme ve sekme karakterleri alanları dönüştürür ve ardından bir boşluk varsa korur bitişik bir dize ya da sonunda bulunan. XAML boşluk işleme tam açıklaması bu konuda ele alınmamıştır. Ayrıntılar için bkz [XAML'de boşluk işleme](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>İşaretleme uzantıları  
 Biçimlendirme uzantıları, XAML dili kavramıdır. Bir öznitelik sözdizimi, süslü ayraçlar değeri sağlamak için kullanıldığında (`{` ve `}`) biçimlendirme uzantısı kullanımı gösterir. Bu kullanım öznitelik değerleri genel işlenmesi sabit değerli bir dize veya dize dönüştürülebilir değeri olarak erişmek için işleme XAML yönlendirir.  
  
 Kullanılan en yaygın biçimlendirme uzantıları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama programlama olan [bağlama](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), veri bağlama ifadeleri ve kaynak başvuruları için kullanılan [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) ve [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Biçimlendirme uzantıları kullanarak bu özelliği bir öznitelik sözdizimi genel desteklemiyor olsa bile özelliklerini değerlerini sağlamak için öznitelik sözdizimini kullanabilirsiniz. Biçimlendirme uzantıları ara ifade türleri değerleri ertelemeyi veya yalnızca çalışma zamanında mevcut olan diğer nesnelere başvurma gibi özellikleri etkinleştirmek için çoğunlukla kullanır.  
  
 Örneğin, aşağıdaki biçimlendirme değerini ayarlar <xref:System.Windows.FrameworkElement.Style%2A> öznitelik sözdizimini kullanarak özelliği. <xref:System.Windows.FrameworkElement.Style%2A> Özelliği alır örneği <xref:System.Windows.Style> bir öznitelik sözdizimi dizesiyle örneği oluşturulamadı, varsayılan sınıf. Ancak bu durumda, belirli biçimlendirme uzantısı, öznitelik başvuran [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Bu biçimlendirme uzantısı işlenirken anahtarlı bir kaynak bir kaynak sözlüğü olarak daha önce örneğinin başlatılmasından bir stil bir başvuru döndürür.  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 Özellikle WPF'de XAML uygulanması için bir başvuru tüm biçimlendirme uzantıları listelemek için bkz: [WPF XAML uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md). System.Xaml ve .NET Framework XAML uygulamaları için daha geniş çapta kullanılabilir tarafından tanımlanan biçimlendirme uzantıları başvuru listesi için bkz: [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Biçimlendirme uzantısı kavramları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Tür dönüştürücüleri  
 İçinde [kısa XAML sözdiziminde](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief) bölümünde, öznitelik değeri bir dize ayarlanması için belirtilmiştir. Dizeleri diğer nesne türleri veya ilkel değerler nasıl dönüştürülür, temel, yerel işleme dayalı <xref:System.String> kendisini yazın, ayrıca yerel belirli işleme türleri gibi <xref:System.DateTime> veya <xref:System.Uri>. Ancak birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türleri veya bu türlerde üyeleri genişletmek davranışı, daha karmaşık nesne türlerini örneklerini dizeler ve öznitelikleri belirtilebilir şekilde işleme temel dize özniteliği.  
  
 <xref:System.Windows.Thickness> Yapısı için XAML kullanımları etkin bir tür dönüştürme türün bir örneği verilmiştir. <xref:System.Windows.Thickness> içinde yuvalanmış dikdörtgene ölçümleri gösterir ve değeri olarak gibi özellikler için kullanılan <xref:System.Windows.FrameworkElement.Margin%2A>. Tür dönüştürücüsünü yerleştirerek tarafından <xref:System.Windows.Thickness>, kullanan tüm özellikleri bir <xref:System.Windows.Thickness> öznitelik olarak belirtilen çünkü XAML'de belirtmek daha kolay olur. Aşağıdaki örnek için bir değer sağlamak için bir tür dönüştürme ve öznitelik sözdizimi kullanır bir <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 Önceki öznitelik sözdizimi örneği şuna eşdeğerdir daha ayrıntılı sözdizimi örneği burada <xref:System.Windows.FrameworkElement.Margin%2A> yerine aracılığıyla öğesi sözdizimi içeren özellik kümesi bir <xref:System.Windows.Thickness> object öğesi. Dört anahtar özelliklerini <xref:System.Windows.Thickness> olarak öznitelikleri yeni örneğinde ayarlanır:  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Tür dönüştürme türü varsayılan bir oluşturucu sahip olmadığından bir özelliği bu tür bir alt sınıfı karıştırılmaksızın ayarlamak için yalnızca genel yol olduğu nesneleri sınırlı sayıda vardır. Örnek <xref:System.Windows.Input.Cursor>.  
  
 Sözdizimi desteklenip desteklenmediğini ne tür dönüştürmeleri ve kullanımı için öznitelik hakkında daha fazla bilgi için bkz: [TypeConverters ve XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML kök öğeleri ve XAML ad uzayları  
 XAML dosyası hem bir doğru biçimlendirilmiş olması için yalnızca tek bir kök öğe bulunmalıdır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosya ve geçerli bir XAML dosyası. Tipik WPF senaryoları için WPF uygulaması modelinde belirgin bir anlamı olan bir kök öğe kullanın (örneğin, <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> bir sayfa için <xref:System.Windows.ResourceDictionary> bir dış sözlüğü için veya <xref:System.Windows.Application> uygulama tanımı için). İçin tipik bir XAML dosyasının kök öğesinin aşağıdaki örnekte bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasıyla kök öğesinin <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 Kök öğesi de özniteliklerini içeren `xmlns` ve `xmlns:x`. XAML ad uzayları öğeleri olarak işaretleme başvurur türleri yedekleme için tür tanımları içeren bir XAML işlemciye bu öznitelikleri gösterir. `xmlns` Öznitelik özellikle varsayılan XAML ad uzayı gösterir. Varsayılan XAML ad uzayı içinde nesne öğeleri biçimlendirmede bir önek belirtilebilir. Çoğu için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama senaryoları ve neredeyse tüm verilen örnekler için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bölümlerini [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], varsayılan XAML ad uzayı eşlenmiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ad alanı [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]. `xmlns:x` Öznitelik, XAML dili ad eşleyen bir ek XAML ad uzayı gösterir [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 Bu kullanımı `xmlns` kullanım ve bir isim alanı eşlemesi için kapsamını tanımlamak için XML 1.0 belirtimi ile tutarlıdır. XAML ad kapsamları, yalnızca XAML isim alanı de tür çözümleme ve XAML ayrıştırma geldiğinde isim alanı'nın öğeleri türlerine göre nasıl yedeklenen hakkında bir şey anlamına gelir, XML ad kapsamları farklıdır.  
  
 Unutmayın `xmlns` öznitelikleridir yalnızca her XAML dosyasının kök öğesinin kesinlikle gerekli. `xmlns` tanımları kök öğesinin tüm alt öğelerine uygulanır (Bu davranış yeniden XML 1.0 belirtimi için tutarlı `xmlns`.) `xmlns` öznitelikler de diğer öğeleri kök altında izin verilen ve tanımlama öğesinin alt herhangi bir öğenin geçerli olur. Ancak, sık tanımı veya XAML ad uzayları şemadaki okunması zor olan bir XAML biçimlendirme stili neden olabilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemcisinin uygulaması WPF çekirdek derlemelerin tanıma sahip bir altyapı içerir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Çekirdek derlemeler bilinen destekleyen türler içerecek şekilde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan XAML ad uzayı eşlemeleri. Bu proje yapınızın parçası olan yapılandırma aracılığıyla etkinleştirilir dosya ve WPF derleme ve proje sistemleri. Bu nedenle, varsayılan olarak varsayılan XAML ad uzayı bildirme `xmlns` alınması XAML öğeleri başvurmak için gerekli olan tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler.  
  
### <a name="the-x-prefix"></a>Önek x:  
 Önceki örnekte kök öğesi, önek `x:` XAML ad uzayı eşlemek için kullanılan [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], XAML dili destekleyen ayrılmış XAML ad uzayı olduğu oluşturur. Bu `x:` önek bu XAML ad uzayı projeleri için şablonlar, örnekler ve bu belgelerinde eşlemek için kullanılan [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. XAML dili için XAML ad alanı, XAML'de çok sık kullanacağınız çeşitli programlama yapılarını içerir. En yaygın bir listesi aşağıda verilmiştir `x:` kullanacağınız programlama yapıları öneki:  
  
-   [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md): her kaynak için benzersiz bir anahtar ayarlar bir <xref:System.Windows.ResourceDictionary> (veya diğer çerçeveler benzer sözlük kavramlar). `x:Key` büyük olasılıkla % 90'ını hesabı olacak `x:` kullanımları bir tipik WPF uygulamanın biçimlendirmede görürsünüz.  
  
-   [x: Class](../../../../docs/framework/xaml-services/x-class-directive.md): belirtir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] XAML sayfası için arka plan kodu sağlayan sınıf için ad alanını ve sınıf adı. Arka plan kodu WPF programlama modeli başına desteklemek için sınıf olması gerekir ve bu nedenle, neredeyse her zaman görürsünüz `x:` hiçbir kaynak olsa bile, eşlenmiş.  
  
-   [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md): nesne öğesindeki işlendikten sonra çalışma zamanı kodu mevcut örneği için bir çalışma zamanı nesne adını belirtir. Genel olarak, WPF tanımlı eşdeğer özelliğini sık kullanacağınız [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md). Gibi özellikleri özellikle özelliğini destekleyen bir CLR eşlemeniz ve dolayısıyla sık çalışma zamanı kodu başlatılmış XAML adlandırılmış öğeleri bulmak için kullandığınız uygulama programlama için daha kullanışlıdır. En sık karşılaşılan böyle bir özellik olan <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>. Hala kullanabilir [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) zaman eşdeğer WPF çerçeve düzeyi <xref:System.Windows.FrameworkElement.Name%2A> özelliği, belirli bir türü desteklenmiyor. Bu, belirli animasyon senaryolarda ortaya çıkar.  
  
-   [x: Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md): XAML uyumlu özelliği aksi değil statik bir değer döndüren bir başvuru sağlar.  
  
-   [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md): oluşturan bir <xref:System.Type> tabanlı bir tür adına başvurusu. Bu öznitelikler belirtmek için kullanılan <xref:System.Type>, gibi <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>, sık özelliği yerel dize olsa-için-<xref:System.Type> şekilde dönüştürmede, [x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) biçimlendirme uzantısı kullanımı İsteğe bağlı.  
  
 Vardır yapılardan programlama ek `x:` gibi ortak olmayan önek/XAML ad uzayı. Ayrıntılar için bkz [XAML Namespace (x:) Dil özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Özel ön ekleri ve XAML'de özel türler  
 Kendi özel derlemeler için ya da PresentationCore, PresentationFramework ve WindowsBase WPF çekirdek dışında derlemeler için özel bir parçası olarak derleme belirtebilirsiniz `xmlns` eşleme. Bu tür denediğiniz XAML kullanımları desteklemek için doğru bir şekilde uygulandığından sürece, XAML'de bütünleştirilmiş koddan türleri sonra başvurabilirsiniz.  
  
 XAML biçimlendirme nasıl özel önekleri iş çok basit bir örnek verilmiştir. Önek `custom` kök öğe etiketinde tanımlanan ve paketlenmiş ve uygulama ile kullanılabilen belirli bir derleme eşlenir. Bu derleme bir türünü içeren `NumericUpDown`, genel XAML kullanımı yanı sıra, ekleme, bu belirli bir noktada bir WPF XAML içerik modelinde izin veren bir sınıf devralma kullanarak desteklemek için uygulanır. Bu örneği `NumericUpDown` denetim object öğesi bildirilen, böylece hangi XAML XAML ayrıştırıcısı bilir önek kullanarak ad alanı türü içerir ve bu nedenle burada yedekleme derleme, tür tanımı içeren.  
  
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
  
 XAML'de Özel türleri hakkında daha fazla bilgi için bkz: [XAML ve WPF için özel sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
 XML ad alanları ve derlemeler yedeklemenin kodda ad alanlarını nasıl ilişkili olduğunu hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML Namespace eşleme](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>Olaylar ve XAML arka plan kodu  
 Çoğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML biçimlendirme ve arka plan kodu uygulamaları oluşur. Bir projede XAML olarak yazılmış bir `.xaml` dosyası ve bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dil Microsoft Visual Basic veya C# gibi bir arka plan kod dosyasına yazma için kullanılır. XAML dosyası WPF programlama ve uygulama modelleri bir parçası olarak derlenmiş biçimlendirme, XAML arka plan kod konumunu bir ad alanı belirterek XAML dosyası tanımlanan dosya ve olarak sınıf `x:Class` XAML kök öğesinin özniteliği.  
  
 Örneklerde şu ana kadar birçok düğme gördünüz, ancak bu düğmeleri hiçbiri henüz ilişkili tüm mantıksal davranışını vardı. Bir nesne öğesi için bir davranış eklemek için birincil uygulama düzeyi var olan bir olaya öğesi sınıfının kullanın ve çalışma zamanında olay ortaya çıktığında çağrılan bu olay için belirli bir işleyicinin yazmak için mekanizmadır. İşleyicinizi uygulayan kod kod arkasında tanımlandı ancak olay adı ve kullanılacak işleyicisi adı biçimlendirmede belirtilir.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Arka plan kod dosyasının CLR ad kullandığına dikkat edin `ExampleNamespace` ve bildirir `ExamplePage` bu ad alanı içindeki bir parçalı sınıf olarak. Bu parallels `x:Class` öznitelik değerini `ExampleNamespace`.`ExamplePage` Biçimlendirme kök dizininde sağlandı. Kök öğesi türünden sınıf türetme tarafından WPF biçimlendirme derleyici derlenmiş herhangi bir XAML dosyası için bir parçalı sınıf oluşturun. Ayrıca aynı kısmi sınıfı tanımlayan arka plan kod sağladığınızda, sonuç kodu aynı ad alanına ve derlenmiş uygulama sınıfının içinde birleştirilir.  
  
 WPF'de arka plan kodu programlama gereksinimleri hakkında daha fazla bilgi için "arka plan kodu, olay işleyicisi ve parçalı sınıf gereksinimleri" bölümüne bakın [arka plan kod ve WPF XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
 Ayrıca, ayrı arka plan kodu dosyası oluşturmak istemiyorsanız, satır içi XAML dosyası kodunuzda erişebilirsiniz. Ancak, satır içi kod önemli sınırlamalar vardır daha az verimli bir yöntem gerekir. Ayrıntılar için bkz [arka plan kod ve WPF XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
### <a name="routed-events"></a>Yönlendirilmiş olaylar  
 Belirli bir olay özelliği için temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilmiş bir olaydır. Olayları etkinleştir bir ağaç ilişkisi bağlı öğeleri sürece farklı bir öğe tarafından başlatılan bir olayını işlemek için bir öğe yönlendirilir. Olay işleme XAML özniteliğiyle belirtirken, yönlendirilmiş olay için kulak ve belirli bir olay sınıfı üyeleri tablosunda listelemez öğeler de dahil olmak üzere herhangi bir öğe üzerinde işlenmiş. Bu, sahibi olan sınıf adı olay adı özniteliğiyle niteleme tarafından gerçekleştirilir. Örneğin, üst `StackPanel` sürekli olarak `StackPanel`  /  `Button` örnek alt öğesi düğmenin için bir işleyici kaydetmek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öznitelik belirterek olay `Button.Click` üzerinde `StackPanel` Nesne öğe, öznitelik değeri olarak işleyici adınız. Nasıl yönlendirilmiş olayları çalışma hakkında daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>XAML öğeleri adlı  
 Varsayılan olarak, benzersiz bir kimlik veya nesne başvurusu bir nesne grafiğinin XAML nesne öğesi işleme tarafından oluşturulan nesne örneği sahip değil. Kodda bir oluşturucu çağırırsanız, daha sonra kodunuzda örneği başvurabilmek buna karşılık, neredeyse her zaman Oluşturucusu sonuç için oluşturulan örnek, bir değişken ayarlamak üzere kullandığınız. XAML biçimlendirme tanımıyla oluşturulan nesneleri için standartlaştırılmış bir erişim sağlamak amacıyla tanımlar [x: Name özniteliği](../../../../docs/framework/xaml-services/x-name-directive.md). Değerini ayarlayabilirsiniz `x:Name` herhangi bir nesne öğesi özniteliği. Arka plan kod içinde seçtiğiniz tanımlayıcısı için oluşturulan örnek başvuran bir örnek değişkeni eşdeğerdir. Tüm yönden öğeleri işlevi (Bu örnek adına başvuran) nesne örneklerini oldukları ve, arka plan kodu uygulama içinde çalışma zamanı etkileşimleri işlemek için adlandırılmış öğelere başvurabilir sanki adlı. Örnekler ve değişkenler arasındaki bu bağlantı WPF XAML biçimlendirme derleyici tarafından gerçekleştirilir ve daha fazla özellikle özellikleri ve desenler gibi ilgili <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> , değil açıklanır bu konudaki ayrıntılı.  
  
 WPF çerçeve düzeyi XAML öğeleri devralan bir <xref:System.Windows.FrameworkElement.Name%2A> tanımlanan XAML eşdeğerdir özelliği `x:Name` özniteliği. Belirli bir sınıf özelliği düzeyi eşdeğerleri de sağlar `x:Name`, aynı zamanda genellikle tanımlanmış olarak bir `Name` özelliği. Bulamazsa, genellikle, konuşma bir `Name` özelliği, seçilen öğeyi/türünüz için kullanım üyeleri tablosundaki `x:Name` yerine. `x:Name` Değerleri, çalışma zamanında belirli alt sistemleri veya yardımcı program yöntemleri tarafından gibi kullanılabilir bir XAML öğesinde tanımlayıcı sağlayacaktır <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.FrameworkElement.Name%2A> üzerinde bir <xref:System.Windows.Controls.StackPanel> öğesi. Ardından, bir işleyici bir <xref:System.Windows.Controls.Button> içindeki <xref:System.Windows.Controls.StackPanel> başvuruları <xref:System.Windows.Controls.StackPanel> örneği başvurusu aracılığıyla `buttonContainer` tarafından ayarlanmış <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 Böylece adları tahmin edilebilir olan belirli bir kapsamdaki içinde benzersiz olması zorunlu bir değişken gibi yalnızca bir örneği için XAML ad kapsamı, bir kavramı tarafından tabidir. Bir sayfayı tanımlayan birincil biçimlendirme XAML isim alanı sınır bu sayfanın kök öğesi olan bir benzersiz XAML isim alanı, gösterir. Ancak, diğer biçimlendirme kaynakları içeren bir sayfa stilleri veya şablonları stiller içinde gibi çalışma zamanında etkileşim kurabilir ve böyle biçimlendirme kaynakları genellikle mutlaka sayfa XAML isim alanı ile bağlanmayan kendi XAML ad kapsamları sahiptir. Daha fazla bilgi için `x:Name` ve XAML ad kapsamları Bkz <xref:System.Windows.FrameworkElement.Name%2A>, [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md), veya [WPF XAML ad kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>Ekli özellikler ve ekli olaylar  
 XAML belirli özellikler ya da özellik veya olay üzerinde değer belirlendi öğe için tür tanımları içinde var olup bağımsız olarak herhangi bir öğe üzerinde belirtilen olayları sağlayan bir dil özellik belirtir. Bu özelliği Özellikler sürümü iliştirilmiş bir özellik olarak adlandırılır, olayları sürüm ekli olay adı verilir. Kavramsal olarak, tüm XAML öğe/nesnesi örneğinde ayarlanabilir genel üye olarak ekli özellikler ve ekli olaylar düşünebilirsiniz. Ancak, bu öğe/sınıfı veya daha büyük bir altyapısı yedekleme özellik deposu ekli değerlerini desteklemesi gerekir.  
  
 XAML'de ekli özellikler genellikle öznitelik sözdizimi kullanılır. Öznitelik sözdiziminde iliştirilmiş bir özellik biçiminde belirtin *ownerType*. *propertyName*.  
  
 Yüzeysel olarak, bu özellik öğesi kullanımı benzer, ancak bu durumda *ownerType* belirttiğiniz olduğundan her zaman object öğesi farklı bir type ekli özellik nerede ayarlanır. *ownerType* alın veya ekli özellik değerini ayarlamak için XAML işlemcisi tarafından gerekli erişimci yöntemlerini sağlar türüdür.  
  
 Ekli özellikler için en yaygın senaryo, kendi üst öğesi bir özellik değeri bildirmek alt öğeler etkinleştirmektir.  
  
 Aşağıdaki örnek gösterilmektedir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> özelliği eklenmiş. <xref:System.Windows.Controls.DockPanel> Sınıfı tanımlayan erişimcileri <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ve bu nedenle ekli özelliğe sahip. <xref:System.Windows.Controls.DockPanel> Sınıfı de içerir ve alt öğeleri tekrarlanan ve özellikle her öğe için kümesi değerini denetler mantığı <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Bir değer bulunursa, o değer alt öğeleri konumlandırmak için Düzen sırasında kullanılır. Kullanımı <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özellik ve bu konumlandırma yeteneği olan aslında seçimini artıran senaryo için <xref:System.Windows.Controls.DockPanel> sınıfı.  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], çoğu veya tamamı ekli özellikler bağımlılık özellikleri olarak da uygulanır. Ayrıntılar için bkz [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Ekli olaylar kullanın benzer *ownerType*. *eventName* öznitelik sözdizimi biçimidir. Yalnızca ekli olmayan olaylar gibi ekli olay XAML'de öznitelik değeri olayı öğede ele alındığında çağrılan işleyici yöntem adını belirtir. WPF XAML içinde ekli olay kullanımları daha az yaygındır. Daha fazla bilgi için bkz: [bağlı olaylara genel bakış](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>Taban türleri ve XAML  
 Temel alınan WPF XAML ve onun XAML ad uzayı koleksiyonudur karşılık türleri [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri için XAML biçimlendirme öğeleri yanı sıra. Ancak, tüm sınıflar öğelerine eşlenebilir. Soyut sınıflar, gibi <xref:System.Windows.Controls.Primitives.ButtonBase>, ve belirli soyut taban sınıfları devralma için kullanılan [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne modeli. Somut XAML öğelerin her biri kendi hiyerarşideki bazı temel sınıfından üyeleri devralındığından soyut olanlar da dahil olmak üzere temel sınıflar XAML geliştirme için hala önemlidir. Genellikle bu üyeleri olarak öznitelikleri öğede ayarlanabilir özellikleri veya işlenebilir olayları içerir. <xref:System.Windows.FrameworkElement> somut temeli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sınıfının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] WPF framework düzeyinde. Tasarlarken [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]kullanacağı çeşitli şekil, paneli, oluşturma öğesi veya denetim sınıfları, tüm türetilen <xref:System.Windows.FrameworkElement>. İlgili bir temel sınıf <xref:System.Windows.FrameworkContentElement>, iyi bir akış düzeni sunumu için iş belge yönelimli öğeleri destekler kullanarak [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , kasıtlı olarak yansıtmak [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] içinde <xref:System.Windows.FrameworkElement>. Öğe düzeyinde özniteliklerinin birleşimi ve [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne modeli belirli XAML öğesi ve temel alınan türü ne olursa olsun en somut XAML öğelerde ayarlanabilir ortak özellikler kümesi ile sağlar.  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML güvenliği  
 XAML doğrudan nesne örnek oluşturma ve yürütme temsil eden bir biçimlendirme dilidir. Bu nedenle, XAML'de oluşturulan öğeleri aynı oluşturulan eşdeğer olarak (ağ erişimi, dosya sistemi g/ç, örneğin) sistem kaynakları ile etkileşim olanağına sahip kodu yapar.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] destekleyen [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] güvenlik framework [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]. Bunun anlamı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Internet bölgesinde çalışan içeriği yürütme izinleri daha az. "Esnek XAML'i" (derlenmemiş XAML sayfaları yorumlanan yükleme zamanında bir XAML İzleyici tarafından) ve [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] bu Internet bölgesinde genellikle çalıştırılır ve aynı izin kümesi kullanın.  Ancak, barındırma uygulama olduğu gibi tam güvenilen bir uygulamaya yüklenmiş XAML sistem kaynaklarına aynı erişimi vardır. Daha fazla bilgi için bkz: [WPF kısmi güven güvenlik](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>XAML koddan yükleniyor  
 XAML tüm UI tanımlamak için kullanılabilir, ancak bazen de XAML'de UI yalnızca bir parçasını tanımlamak uygundur. Bu özellik, kısmi özelleştirme, bir iş nesnesi ya da çeşitli olası senaryolarda sağlamak için XAML kullanarak bilgileri, yerel depolama etkinleştirmek için kullanılabilir. Bu senaryolar anahtarıdır <xref:System.Windows.Markup.XamlReader> sınıfı ve onun <xref:System.Windows.Markup.XamlReader.Load%2A> yöntemi. Giriş XAML bir dosyadır ve çıktı bu biçimlendirmeden oluşturulmuş çalışma zamanı nesne ağacının tümünü temsil eden bir nesnedir. Sonra uygulama içinde zaten var. başka bir nesnenin bir özellik olarak nesne ekleyebilirsiniz. Özellik nihai görüntüleme yetenekleri olan ve yeni içerik uygulamaya eklendiğini yürütme altyapısı, size bildirir içerik modeldeki uygun bir özellik olduğu sürece kolayca çalışan uygulamanın içeriklerini değiştirme XAML'de göre yükleniyor. Bu özellik genellikle yalnızca çalıştıkları gibi uygulamalara dosyaları yükleme belirgin güvenlik etkilerini nedeniyle tam güven uygulamalarında kullanılabilir olduğunu unutmayın.  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>Sırada ne var?  
 WPF ile olduğu gibi bu konuda XAML sözdizimi kavramları ve terminolojiyi için temel bir giriş sağlar. Burada kullanılan terimler hakkında daha fazla bilgi için bkz: [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Zaten bu yapmadıysanız, öğretici konu alıştırmalarda deneyin [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Öğreticisi tarafından açıklanan biçimlendirme merkezli uygulama oluşturduğunuzda, bu konuda açıklanan kavramları çoğunu pekiştirmek alıştırma yardımcı olur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel alan belirli uygulama modelini kullanan <xref:System.Windows.Application> sınıfı. Ayrıntılar için bkz [uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
 [WPF uygulaması oluşturma](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) XAML dahil uygulamaların komut satırından ve ile nasıl yapılandırıldığı hakkında daha fazla ayrıntı sağlar [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) özelliklerinde yönlülük hakkında daha fazla bilgi veren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve bağımlılık özellikleri kavramını sunmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [WPF için XAML ve Özel Sınıflar](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [XAML Ad Alanı (x:) Dil Özellikleri](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML Uzantıları](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [WPF İçinde Ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
