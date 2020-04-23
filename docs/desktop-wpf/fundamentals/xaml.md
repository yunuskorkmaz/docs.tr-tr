---
title: XAML'ye genel bakış
description: XAML dilinin .NET Core için Windows Presentation Foundation (WPF) tarafından nasıl yapılandırıldığı ve uygulandığını öğrenin.
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
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
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "82071789"
---
# <a name="xaml-overview-in-wpf"></a>WPF'de XAML'ye genel bakış

Bu makalede, XAML dilinin özellikleri açıklanır ve Windows Sunu Temeli (WPF) uygulamalarını yazmak için XAML'yi nasıl kullanabileceğinizi gösterir. Bu makalede, XAML özellikle WPF tarafından uygulandığı şekilde açıklanmaktadır. XAML kendisi WPF daha büyük bir dil kavramıdır.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>XAML nedir

XAML bir bildirimsel biçimlendirme dilidir. .NET Core programlama modeline uygulandığı gibi, XAML bir .NET Core uygulaması için kullanıcı arabirimi oluşturmayı kolaylaştırır. Bildirimsel XAML biçimlendirmesinde görünür UI öğeleri oluşturabilir ve sonra kısmi sınıf tanımları aracılığıyla biçimlendirmeye katılan kod arkası dosyaları kullanarak ui tanımını çalışma zamanı mantığından ayırabilirsiniz. XAML, derlemelerde tanımlanan belirli bir destek türü kümesindeki nesnelerin anlık durumunu doğrudan temsil eder. Bu, genellikle bir destek türü sistemine bu kadar doğrudan bağlı olmayan yorumlanmış bir dil olan diğer biçimlendirme dillerinin çoğundan farklı olarak yapılır. XAML, farklı olabilecek araçları kullanarak ayrı tarafların UI ve uygulama mantığı üzerinde çalışabilecekleri bir iş akışı sağlar.

Metin olarak temsil edildiğinde, XAML dosyaları genellikle `.xaml` uzantıya sahip XML dosyalarıdır. Dosyalar herhangi bir XML kodlamatarafından kodlanabilir, ancak UTF-8 olarak kodlama tipiktir.

Aşağıdaki örnek, bir ui parçası olarak bir düğme yi nasıl oluşturabileceğinizi gösterir. Bu örnek, XAML'nin ortak u-u-u oyalama metaforlarını nasıl temsil ettiğini (tam bir örnek değildir) nasıl bir tat vermek için tasarlanmıştır.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Kısaca XAML sözdizimi

Aşağıdaki bölümlerde XAML sözdiziminin temel formları açıklanve kısa bir biçimlendirme örneği verecektir. Bu bölümler, her sözdizimi formu hakkında, bunların destek türü sisteminde nasıl temsil edildiği gibi tam bilgi sağlamak için tasarlanmamıştır. XAML sözdiziminin özellikleri hakkında daha fazla bilgi için [Bkz.](../../framework/wpf/advanced/xaml-syntax-in-detail.md)

XML dili ile daha önce aşinalık varsa sonraki birkaç bölümde malzeme çok sizin için temel olacaktır. Bu, XAML'nin temel tasarım ilkelerinden birinin bir sonucudur. XAML dili kendi kavramlarını tanımlar, ancak bu kavramlar XML dili ve biçimlendirme formu içinde çalışır.

### <a name="xaml-object-elements"></a>XAML nesne elemanları

Bir nesne öğesi genellikle bir tür örneği bildirir. Bu tür, dil olarak XAML kullanan teknoloji tarafından başvurulan derlemelerde tanımlanır.

Nesne öğesi sözdizimi her zaman`<`bir açılış açısı ayraç ile başlar ( . Bunu, bir örnek oluşturmak istediğiniz türün adı takip edilir. (Ad bir önek, daha sonra açıklanacaktır bir kavram içerebilir.) Bundan sonra, isteğe bağlı olarak nesne öğesi özniteliklerini bildirebilirsiniz. Nesne öğesi etiketini tamamlamak için, kapanış`>`açısı ayraç ( ). Bunun yerine, etiketi ileri eğik çizgi ve kapatma açısı braketi ile art arda tamamlayarak, içeriği olmayan kendi kendine kapatma formu kullanabilirsiniz (`/>`). Örneğin, daha önce gösterilen biçimlendirme snippet tekrar bak.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Bu iki nesne öğesini `<StackPanel>` belirtir: (içerik ve daha `<Button .../>` sonra bir kapanış etiketi ile) ve (kendi kendine kapatma formu, birkaç öznitelikleri ile). Nesne öğeleri `StackPanel` `Button` ve WPF tarafından tanımlanan ve WPF derlemelerinin bir parçası olan bir sınıfın adına her harita. Bir nesne öğesi etiketi belirttiğiniz zaman, alttaki türün yeni bir örneğini oluşturmak için XAML işleme için bir yönerge oluşturursunuz. Her örnek, XAML'yi ayrıştırırken ve yüklerken alttaki türün parametresiz oluşturucusu çağırılarak oluşturulur.

### <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (özellikler)

Bir nesnenin özellikleri genellikle nesne öğesinin öznitelikleri olarak ifade edilebilir. Öznitelik sözdizimi, ayarlanan nesne özelliğini adlandırır ve ardından atama işleci (=) tarafından belirlenir. Bir öznitelik değeri her zaman tırnak işaretleri içinde bulunan bir dize olarak belirtilir.

Öznitelik sözdizimi en akıcı özellik ayarı sözdizimidir ve geçmişte biçimlendirme dillerini kullanmış olan geliştiriciler için kullanılacak en sezgisel sözdizimidir. Örneğin, aşağıdaki biçimlendirme, `Content`kırmızı metin ve mavi arka plan olarak belirtilen metni görüntülemek için bir düğme oluşturur.

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Özellik öğesi sözdizimi

Bir nesne öğesinin bazı özellikleri için, özellik değerini sağlamak için gerekli nesne veya bilgi tırnak işareti ve öznitelik sözdizimi dize kısıtlamaları içinde yeterince ifade edilemediği için öznitelik sözdizimi mümkün değildir. Bu gibi durumlarda, özellik öğesi sözdizimi olarak bilinen farklı bir sözdizimi kullanılabilir.

Özellik öğesi başlangıç etiketiiçin sözdizimi. `<TypeName.PropertyName>` Genellikle, bu etiketin içeriği özelliğin değeri olarak aldığı türün nesne öğesidir. İçeriği belirttikten sonra, özellik öğesini bir bitiş etiketiyle kapatmanız gerekir. Bitiş etiketinin sözdizimi `</TypeName.PropertyName>`.

Bir öznitelik sözdizimi mümkünse, öznitelik sözdizimini kullanmak genellikle daha uygundur ve daha kompakt bir biçimlendirme sağlar, ancak bu genellikle teknik bir sınırlama değil, yalnızca bir stil meselesidir. Aşağıdaki örnekte, önceki öznitelik sözdizimi örneğinde olduğu gibi ayarlanan aynı özellikleri gösterir, ancak `Button`bu kez tüm özellikleri için özellik öğesi sözdizimi kullanarak .

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Toplama sözdizimi

XAML dili, daha fazla insan tarafından okunabilir biçimlendirme üreten bazı optimizasyonlar içerir. Böyle bir optimizasyon, belirli bir özellik bir toplama türü alırsa, o özelliğin değeri içindeki alt öğeler olarak biçimlendirme de beyan ettiğiniz öğelerin koleksiyonun bir parçası haline gelmesidir. Bu durumda alt nesne öğeleri koleksiyonu koleksiyon özelliğine ayarlanan değerdir.

Aşağıdaki örnek, özelliğin <xref:System.Windows.Media.GradientBrush.GradientStops%2A> değerlerini ayarlamak için koleksiyon sözdizimini gösterir.

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.GradientStops>
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->
    <GradientStop Offset="0.0" Color="Red" />
    <GradientStop Offset="1.0" Color="Blue" />
  </LinearGradientBrush.GradientStops>
</LinearGradientBrush>
```

### <a name="xaml-content-properties"></a>XAML içerik özellikleri

XAML, bir sınıfın özelliklerinden birini XAML _içerik_ özelliği olarak tam olarak belirleyebileceği bir dil özelliği belirtir. Bu nesne öğesinin alt öğeleri, bu içerik özelliğinin değerini ayarlamak için kullanılır. Başka bir deyişle, benzersiz içerik özelliği için, XAML biçimlendirmesinde bu özelliği ayarlarken bir özellik öğesini atlayabilir ve biçimlendirmede daha görünür bir üst/alt metafor oluşturabilirsiniz.

Örneğin, <xref:System.Windows.Controls.Border> bir _içerik_ özelliği <xref:System.Windows.Controls.Decorator.Child%2A>belirtir. Aşağıdaki iki <xref:System.Windows.Controls.Border> öğe aynı şekilde ele alınır. İlki içerik özelliği sözdiziminden yararlanır ve `Border.Child` özellik öğesini atlar. İkincisi açıkça `Border.Child` gösterir.

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

XAML dilinin bir kuralı olarak, xaml içerik özelliğinin değeri, bu nesne öğesindeki diğer özellik öğelerinden önce veya tamamen önce veya sonra verilmelidir. Örneğin, aşağıdaki biçimlendirme derlemez.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

XAML sözdiziminin özellikleri hakkında daha fazla bilgi için [Bkz.](../../framework/wpf/advanced/xaml-syntax-in-detail.md)

### <a name="text-content"></a>Metin içeriği

Az sayıda XAML öğesi metni doğrudan içerik olarak işleyebilir. Bunu etkinleştirmek için aşağıdaki durumlardan birinin doğru olması gerekir:

- Sınıf bir içerik özelliği bildirmelidir ve bu içerik özelliği bir dize atilebilen <xref:System.Object>bir tür olmalıdır (tür olabilir). Örneğin, herhangi <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.Content%2A> bir içerik özelliği olarak <xref:System.Object>herhangi bir kullanım ve türü <xref:System.Windows.Controls.ContentControl> , <xref:System.Windows.Controls.Button>ve `<Button>Hello</Button>`bu gibi bir aşağıdaki kullanımı destekler: .

- Tür, bir tür dönüştürücü bildirmelidir, bu durumda metin içeriği bu tür dönüştürücü için başlatma metni olarak kullanılır. Örneğin, `<Brush>Blue</Brush>` içerik değerini bir `Blue` fırçaya dönüştürür. Bu durum pratikte daha az yaygındır.

- Türü bilinen bir XAML dili ilkel olmalıdır.

### <a name="content-properties-and-collection-syntax-combined"></a>İçerik özellikleri ve koleksiyon sözdizimi birleştirildi

Bu örneği göz önünde bulundurun.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Burada, <xref:System.Windows.Controls.Button> her bir çocuk <xref:System.Windows.Controls.StackPanel>unsurudur. Bu, iki farklı nedenden dolayı iki etiketi atlayan akıcı ve sezgisel bir biçimlendirmedir.

- **Atlanan StackPanel.Children özellik öğesi:** <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>xaml içerik özelliği <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> olarak tanımlar.

- **Atlanan UIElementCollection nesne öğesi:** Özellik, <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> uygulayan <xref:System.Windows.Controls.UIElementCollection>türü <xref:System.Collections.IList>alır. Koleksiyonun öğe etiketi, <xref:System.Collections.IList>'. gibi koleksiyonları işlemek için XAML kurallarına göre atlanabilir. (Bu durumda, <xref:System.Windows.Controls.UIElementCollection> parametresiz bir oluşturucu ortaya çıkarmadığından ve <xref:System.Windows.Controls.UIElementCollection> bu nedenle nesne öğesi yorumlandı gösterilir.

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

Öznitelik sözdizimi, özellik yerine olay olan üyeler için de kullanılabilir. Bu durumda, özniteliğin adı olayın adıdır. XAML için olayların WPF uygulamasında, öznitelik değeri bu olayın temsilcisi ni uygulayan bir işleyicinin adıdır. Örneğin, aşağıdaki biçimlendirme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay için bir işleyiciyi <xref:System.Windows.Controls.Button> biçimlendirmede oluşturulan bir işleyiciatar:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

WPF'deki olaylar ve XAML, öznitelik sözdiziminin bu örneğinden daha fazladır. Örneğin, burada başvurulan `ClickHandler` kişinin neyi temsil ettiğinizi ve nasıl tanımlandığını merak edebilirsiniz. Bu, bu makalenin yaklaşan [Olaylar ve XAML kod arkası](#events-and-xaml-code-behind) bölümünde açıklanacaktır.

## <a name="case-and-white-space-in-xaml"></a>XAML'de kasa ve beyaz boşluk

Genel olarak, XAML büyük/küçük harf duyarlıdır. Destek türlerini çözmek amacıyla WPF XAML, CLR'nin büyük/küçük harf duyarlı olduğu kurallara göre büyük/küçük harf duyarlıdır. Nesne öğeleri, özellik öğeleri ve öznitelik adlarının tümü, ada göre montajdaki alttaki türe veya bir türün üyesiyle karşılaştırıldığında hassas kasa kullanılarak belirtilmelidir. XAML dil anahtar kelimeleri ve ilkel de büyük/küçük harf duyarlıdır. Değerler her zaman büyük/küçük harf duyarlı değildir. Değerler için büyük/küçük harf duyarlılığı, değeri alan özellik veya özellik değeri türüyle ilişkili tür dönüştürücü davranışına bağlıdır. <xref:System.Boolean> Örneğin, türü alan özellikler, yalnızca `true` `True` yerel WPF XAML parser türü dönüştürme zaten <xref:System.Boolean> eşdeğerolarak bu izin verir, çünkü ya da eşdeğer değerler olarak alabilir.

WPF XAML işlemciler ve serializers yoksaymak veya tüm önemsiz beyaz boşluk bırakın ve herhangi bir önemli beyaz boşluk normalleştirir. Bu, XAML belirtiminin varsayılan beyaz alan davranış önerileriyle tutarlıdır. Bu davranış, yalnızca XAML içerik özellikleri içindeki dizeleri belirttiğiniz zaman ortaya atılır. En basit ifadeyle, XAML boşluk, satır akışı ve sekme karakterlerini boşluklara dönüştürür ve bitişik bir dize sonunda bulunursa bir alanı korur. XAML beyaz alan işlemetam açıklama bu makalede ele alınmaz. Daha fazla bilgi için [XAML'deki Beyaz alan işleme](../xaml-services/white-space-processing.md)ye bakın.

## <a name="markup-extensions"></a>İşaretleme uzantıları

Biçimlendirme uzantıları bir XAML dil kavramıdır. Öznitelik sözdizimi değerini sağlamak için kullanıldığında, kıvırcık ayraçlar (`{` ve `}`) bir biçimlendirme uzantısı kullanımını gösterir. Bu kullanım, XAML işlemini öznitelik değerlerinin genel işlemden gerçek bir dize veya dize dönüştürülebilir değer olarak kaçmasına yönlendirir.

WPF uygulama programlamasında kullanılan en yaygın biçimlendirme [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)uzantıları, veri bağlama ifadeleri ve [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md)kaynak başvuruları ve . Biçimlendirme uzantılarını kullanarak, özellik genel olarak bir öznitelik sözdizimini desteklemese bile, özellikler için değerler sağlamak için öznitelik sözdizimini kullanabilirsiniz. Biçimlendirme uzantıları genellikle değerleri erteleme veya yalnızca çalışma zamanında bulunan diğer nesnelere başvurma gibi özellikleri etkinleştirmek için ara ifade türlerini kullanır.

Örneğin, aşağıdaki biçimlendirme öznitelik sözdizimini kullanarak özelliğin <xref:System.Windows.FrameworkElement.Style%2A> değerini ayarlar. Özellik, <xref:System.Windows.FrameworkElement.Style%2A> varsayılan olarak <xref:System.Windows.Style> bir öznitelik sözdizimi dize tarafından instantiated olamazdı sınıf, bir örnek alır. Ancak bu durumda, öznitelik belirli bir biçimlendirme uzantısı başvurur. `StaticResource` Bu biçimlendirme uzantısı işlendiğinde, kaynak sözlüğünde anahtarlı kaynak olarak daha önce anında bulunan bir stil için bir başvuru döndürür.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Özellikle WPF'de uygulanan XAML için tüm biçimlendirme uzantılarının başvuru listesi için [Bkz.](../../framework/wpf/advanced/wpf-xaml-extensions.md) System.Xaml tarafından tanımlanan ve .NET Core XAML uygulamaları için daha yaygın olarak kullanılabilen biçimlendirme uzantılarının başvuru listesi için [Bkz. XAML Namespace (x:) Dil Özellikleri](../xaml-services/namespace-language-features.md). Biçimlendirme uzantısı kavramları hakkında daha fazla bilgi için [bkz.](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)

## <a name="type-converters"></a>Tip dönüştürücüler

Kısa bölümünde [XAML Sözdizimi,](#xaml-syntax-in-brief) öznitelik değeri bir dize tarafından ayarlanabilmesi gerektiği belirtilmiştir. Dizelerin diğer nesne türlerine veya ilkel değerlere <xref:System.String> nasıl dönüştürüldüğünün temel, yerel kullanımı, tür <xref:System.DateTime> deki diğer <xref:System.Uri>türlere ve . Ancak birçok WPF türü veya bu tür in üyeleri, temel dize özniteliği işleme davranışını, daha karmaşık nesne türlerinin örneklerinin dizeleri ve öznitelikleri olarak belirtilebildiği şekilde genişletir.

Yapı, <xref:System.Windows.Thickness> XAML kullanımları için bir tür dönüştürme etkin leştirilmiş bir tür örneğidir. <xref:System.Windows.Thickness>iç içe bir dikdörtgen içindeki ölçümleri gösterir ve . <xref:System.Windows.FrameworkElement.Margin%2A>gibi özellikler için değer olarak kullanılır. Bir tür dönüştürücü <xref:System.Windows.Thickness>yerleştirerek, bir <xref:System.Windows.Thickness> öznitelikleri olarak belirtilebilir, çünkü xaml belirtmek için bir kullanan tüm özellikleri belirtmek daha kolaydır. Aşağıdaki örnek, bir tür dönüştürme ve öznitelik sözdizimi için bir değer sağlamak için <xref:System.Windows.FrameworkElement.Margin%2A>kullanır:

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

Önceki öznitelik sözdizimi örneği, <xref:System.Windows.FrameworkElement.Margin%2A> nesne öğesi içeren <xref:System.Windows.Thickness> özellik öğesi sözdizimi ile ayarlandığı aşağıdaki daha ayrıntılı sözdizimi örneğine eşdeğerdir. Dört temel özelliği <xref:System.Windows.Thickness> yeni örnekte öznitelikler olarak ayarlanır:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Tür dönüştürmenin bir alt sınıf içermeyen bir özelliği bu türe ayarlamanın tek ortak yolu olduğu sınırlı sayıda nesne de vardır, çünkü türün kendisi parametresiz bir oluşturucuya sahip değildir. <xref:System.Windows.Input.Cursor> bunun bir örneğidir.

Tür dönüştürme hakkında daha fazla bilgi için [TypeConverters ve XAML'ye](../../framework/wpf/advanced/typeconverters-and-xaml.md)bakın.

## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML kök öğeleri ve XAML ad alanları

Bir XAML dosyasının hem iyi biçimlendirilmiş bir XML dosyası hem de geçerli bir XAML dosyası olabilmesi için yalnızca bir kök öğesi olması gerekir. <xref:System.Windows.Window> Tipik WPF senaryoları için, WPF uygulama modelinde (örneğin, bir sayfa için, <xref:System.Windows.Controls.Page> <xref:System.Windows.ResourceDictionary> harici sözlük için veya <xref:System.Windows.Application> uygulama tanımı için) belirgin bir anlamı olan bir kök öğesi kullanırsınız. Aşağıdaki örnekte, bir WPF sayfası için tipik bir XAML dosyasının <xref:System.Windows.Controls.Page>kök öğesi ve kök öğesi .

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

Kök öğe de `xmlns` öznitelikleri `xmlns:x`içerir ve . Bu öznitelikler, XAML ad alanlarının biçimlendirmenin öğe olarak başvurulacağı destek türleri için tür tanımlarını içeren bir XAML işlemcisine işaret eder. Öznitelik `xmlns` özellikle varsayılan XAML ad alanını gösterir. Varsayılan XAML ad alanı içinde, biçimlendirmedeki nesne öğeleri önek olmadan belirtilebilir. Çoğu WPF uygulama senaryosu ve SDK'nın WPF bölümlerinde verilen örneklerin hemen hemen hepsi için varsayılan XAML ad alanı `http://schemas.microsoft.com/winfx/2006/xaml/presentation`WPF ad alanına eşlenir. Öznitelik, `xmlns:x` XAML dil ad alanını eşleyen ek bir `http://schemas.microsoft.com/winfx/2006/xaml`XAML ad alanını gösterir.

Bir adskopunun kullanımı ve eşlemi için bir kapsam tanımlamak için bu kullanım `xmlns` XML 1.0 belirtimi ile tutarlıdır. XAML adskopları, yalnızca XAML adskoplarından farklıdır, çünkü bir XAML adskopu, tür çözünürlüğü ve XAML'yi ayrıştma söz konusu olduğunda, adskop öğelerinin türleri tarafından nasıl desteklendirildiğinde niçin desteklendirildiğinde bir şey ima eder.

Öznitelikler, `xmlns` her XAML dosyasının kök öğesi üzerinde yalnızca kesinlikle gereklidir. `xmlns`tanımlar kök öğenin tüm soyundan gelen öğeler için geçerli olacaktır (bu davranış `xmlns`yine XML 1.0 belirtimi ile tutarlıdır .) `xmlns` öznitelikleri de kök altında diğer öğeler üzerinde izin verilir ve tanımlayıcı öğenin herhangi bir soyundan öğeleri için geçerli olacaktır. Ancak, XAML ad alanlarının sık tanımlanması veya yeniden tanımlanması, okunması zor bir XAML biçimlendirme stiline neden olabilir.

XAML işlemcisinin WPF uygulaması, WPF çekirdek montajları konusunda farkında olan bir altyapı içerir. WPF çekirdek derlemelerinin, Varsayılan XAML ad alanına WPF eşlemelerini destekleyen türleri içerdiği bilinmektedir. Bu, proje oluşturma dosyanızın ve WPF yapı ve proje sistemlerinizin bir parçası olan yapılandırma aracılığıyla etkinleştirilir. Bu nedenle, varsayılan XAML ad alanını `xmlns` varsayılan olarak bildirmek, WPF derlemelerinden gelen XAML öğelerine başvurmak için gereken tek şeydir.

### <a name="the-x-prefix"></a>x: önek

Önceki kök öğesi örneğinde önek, `x:` XAML dil yapılarını destekleyen özel XAML ad alanı olan XAML ad alanını `http://schemas.microsoft.com/winfx/2006/xaml`eşlemek için kullanılmıştır. Bu `x:` önek, bu XAML ad alanını projeler için şablonlarda, örneklerde ve bu SDK'daki belgelerde eşleme için kullanılır. XAML dilinin XAML ad alanı, XAML dilinizde sık kullandığınız birkaç programlama yapısı içerir. Kullanacağınız en yaygın `x:` önek programlama yapılarının listesi aşağıda veda edecektir:

- [x:Key](../xaml-services/xkey-directive.md): Her kaynak için bir <xref:System.Windows.ResourceDictionary> (veya diğer çerçevelerde benzer sözlük kavramları) benzersiz bir anahtar ayarlar. `x:Key`muhtemelen tipik bir WPF `x:` uygulamasının biçimlendirmesinde göreceğiniz kullanımların yüzde 90'ını karşılayacaktır.

- [x:Sınıf](../xaml-services/xclass-directive.md): XAML sayfasının kod arkası sağlayan sınıfın CLR ad alanını ve sınıf adını belirtir. WPF programlama modeline göre kod arkası desteklemek için böyle bir sınıfa `x:` sahip olmalısınız ve bu nedenle kaynak olmasa bile hemen hemen her zaman eşlenmiş olarak görürsünüz.

- [x:Ad](../xaml-services/xname-directive.md): Bir nesne öğesi işlendikten sonra çalışma zamanı kodunda bulunan örnek için çalışma zamanı nesne adı belirtir. Genel olarak, [x:Name](../xaml-services/xname-directive.md)için sık sık WPF tanımlı eşdeğer bir özellik kullanırsınız. Bu tür özellikler özellikle bir CLR destek özelliğiyle eşleşir ve böylece, başharfe bürünmüş XAML'den adlandırılmış öğeleri bulmak için sık sık çalışma zamanı kodunu kullandığınız uygulama programlaması için daha kullanışlıdır. En yaygın tür <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>özelliği . Eşdeğer WPF framework düzeyi <xref:System.Windows.FrameworkElement.Name%2A> özelliği belirli bir türde desteklenmiyorsa [x:Name](../xaml-services/xname-directive.md) kullanmaya devam edebilirsiniz. Bu, belirli animasyon senaryolarında oluşur.

- [x:Static](../xaml-services/xstatic-markup-extension.md): XAML uyumlu olmayan statik bir değeri döndüren bir başvurusağlar.

- [x:Type](../xaml-services/xtype-markup-extension.md): Bir <xref:System.Type> tür adına dayalı bir başvuru inşa eder. Bu, [x:Type](../xaml-services/xtype-markup-extension.md) biçimlendirme uzantısı <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>kullanımının isteğe bağlı olacak şekilde<xref:System.Type> sık sık yerel dize-dönüşüme sahip olmasına rağmen, gibi öznitelikleri belirtmek için kullanılır. <xref:System.Type>

`x:` Önek/XAML ad alanında yaygın olmayan ek programlama yapıları vardır. Ayrıntılar için [Bkz. XAML Namespace (x:) Dil Özellikleri](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML'de özel önekler ve özel türler

Kendi özel derlemeleriniz için veya **PresentationCore,** **PresentationFramework** ve **WindowsBase'in**WPF çekirdeği dışındaki derlemeler için, derlemeyi özel `xmlns` bir eşlemenin parçası olarak belirtebilirsiniz. Daha sonra, bu tür çalıştığınız XAML kullanımlarını desteklemek için doğru şekilde uygulandığı sürece, XAML'nizdeki bu derlemeden türlere başvuruyapabilirsiniz.

Aşağıda, XAML biçimlendirmesinde özel öneeklerin nasıl çalıştığına ilgili temel bir örnek verilmiştir. Önek `custom` kök öğe etiketinde tanımlanır ve paketlenen ve uygulamayla birlikte kullanılabilen belirli bir derlemeye eşlenir. Bu derleme, `NumericUpDown`genel XAML kullanımını desteklemek ve wpf XAML içerik modelinde bu özel noktada eklenmesine izin veren bir sınıf kalıtım ı kullanarak uygulanan bir tür içerir. Bu `NumericUpDown` denetimin bir örneği, bir XAML araleminin hangi XAML ad alanını içerdiğini ve bu nedenle de tür tanımını içeren destek derlemesinin nerede olduğunu bilmesi için önek kullanılarak nesne öğesi olarak bildirilir.

```xaml
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

XAML'deki özel türler hakkında daha fazla bilgi için [WPF için XAML ve Özel Sınıflar'a](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)bakın.

Derlemelerde XML ad alanları ve kod ad alanlarının nasıl ilişkili olduğu hakkında daha fazla bilgi [için WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi'ne](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.

## <a name="events-and-xaml-code-behind"></a>Olaylar ve XAML kod arkası

WPF uygulamalarının çoğu hem XAML biçimlendirmesi hem de kod arkası uygulamalarıdır. Proje içinde, XAML bir `.xaml` dosya olarak yazılır ve Microsoft Visual Basic veya C# gibi bir CLR dili kod arkası dosyası yazmak için kullanılır. Bir XAML dosyası WPF programlama ve uygulama modellerinin bir parçası olarak derlendiğinde, XAML dosyası nın XAML dosyasının arka daki XAML `x:Class` dosyasının konumu, XAML'Nin kök öğesinin özniteliği olarak bir ad alanı ve sınıf belirtilerek tanımlanır.

Örneklerde şimdiye kadar, birkaç düğme gördünüz, ancak bu düğmelerin hiçbiri henüz onlarla ilişkili herhangi bir mantıksal davranış vardı. Nesne öğesi için davranış eklemek için birincil uygulama düzeyi mekanizması, öğe sınıfının varolan bir olayını kullanmak ve bu olay çalışma zamanında yükseltildiğinde çağrılan bu olay için belirli bir işleyici yazmaktır. Olay adı ve kullanılacak işleyicinin adı biçimlendirmede belirtilirken, işleyicinizi uygulayan kod kod arkasında tanımlanır.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Kod arkası dosyasının CLR ad alanını `ExampleNamespace` kullandığına `ExamplePage` ve bu ad alanı içinde kısmi bir sınıf olarak beyan ettiğine dikkat edin. Bu, öznitelik `x:Class` değerine `ExampleNamespace`paraleldir.`ExamplePage` biçimlendirme kökünde sağlanmıştır. WPF biçimlendirme derleyicisi, kök öğe türünden bir sınıf türeterek derlenmiş herhangi bir XAML dosyası için kısmi bir sınıf oluşturur. Aynı kısmi sınıfı tanımlayan kod arkası sağladığınızda, ortaya çıkan kod derlenen uygulamanın aynı ad alanı ve sınıfı içinde birleştirilir.

WPF'de kod arkası programlama gereksinimleri hakkında daha fazla bilgi için, [WPF'de Kod Arkası, Olay İşleyicisi ve Kısmi Sınıf Gereksinimleri'ne](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf)bakın.

Ayrı bir kod arkası dosya oluşturmak istemiyorsanız, kodunuzu xaml dosyasında da sıralayabilirsiniz. Ancak, satır satır kodu önemli sınırlamaları olan daha az çok yönlü bir tekniktir. Daha fazla informaiton için [WPF'de Code-Behind ve XAML'ye](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)bakın.

### <a name="routed-events"></a>Yönlendirilen olaylar

WPF için temel olan belirli bir olay özelliği yönlendirilmiş bir olaydır. Yönlendirilen olaylar, öğeler bir ağaç ilişkisi aracılığıyla bağdalı olduğu sürece, bir öğenin farklı bir öğe tarafından yükseltilen bir olayı işlemesini sağlar. XAML özniteliği ile olay işleme belirtirken, yönlendirilen olay, sınıf üyeleri tablosunda belirli bir olayı listelemeyen öğeler de dahil olmak üzere herhangi bir öğe üzerinde dinlenebilir ve işlenebilir. Bu, olay adı özniteliğini sahip sınıf adıyla niteleyerek gerçekleştirilir. Örneğin, devam `StackPanel` eden `StackPanel`  /  `Button` örnekteki üst öğe, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> `Button.Click` `StackPanel` nesne öğesindeki özniteliği belirterek alt öğe düğmesinin olayı için bir işleyici kaydedebilir ve işleyici adınız öznitelik değeri olarak kullanılabilir. Daha fazla bilgi için, [Yönlendirilen Olaylara Genel Bakış'a](../../framework/wpf/advanced/routed-events-overview.md)bakın.

## <a name="xaml-named-elements"></a>XAML adlı öğeler

Varsayılan olarak, bir XAML nesne öğe öğeöğesini işleyerek bir nesne grafiğinde oluşturulan nesne örneği benzersiz bir tanımlayıcı veya nesne başvurusu na sahip değildir. Buna karşılık, kodda bir oluşturucu çağırırsanız, yapılandırılan örneğe bir değişken ayarlamak için hemen hemen her zaman oluşturucu sonucunu kullanırsınız, böylece daha sonra kodunuzda örneğine başvuruyapabilirsiniz. Biçimlendirme tanımı yla oluşturulan nesnelere standart erişim sağlamak için XAML [x:Ad özniteliğini](../xaml-services/xname-directive.md)tanımlar. Öznitelik değerini `x:Name` herhangi bir nesne öğesi üzerinde ayarlayabilirsiniz. Kod arkanızda, seçtiğiniz tanımlayıcı, yapılandırılan örneğe başvuran bir örnek değişkenine eşdeğerdir. Her bakımdan, adlandırılmış öğeler nesne örnekleri (örnek ad başvuruları) gibi işlev görür ve kod arkanızdaki öğeler, uygulama içindeki çalışma zamanı etkileşimlerini işlemek için adlandırılmış öğelere başvurur. Örnekler ve değişkenler arasındaki bu bağlantı WPF XAML biçimlendirme derleyicisi tarafından gerçekleştirilir <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> ve daha spesifik olarak bu makalede ayrıntılı olarak ele alınmayan özellikler ve desenler içerir.

WPF çerçeve düzeyindexaML öğeleri <xref:System.Windows.FrameworkElement.Name%2A> XAML tanımlı `x:Name` öznitelik eşdeğer bir özellik devralır. Bazı diğer sınıflar da için `x:Name`özellik düzeyi eşdeğerleri sağlar , `Name` hangi da genellikle bir özellik olarak tanımlanır. Genel olarak konuşursak, seçtiğiniz `Name` öğe/tür için üyeler tablosunda bir `x:Name` özellik bulamıyorsanız, bunun yerine kullanın. Değerler, `x:Name` çalışma zamanında, belirli alt sistemler veya <xref:System.Windows.FrameworkElement.FindName%2A>.

Aşağıdaki örnek <xref:System.Windows.FrameworkElement.Name%2A> bir <xref:System.Windows.Controls.StackPanel> öğeyi ayarlar. Daha sonra, bir <xref:System.Windows.Controls.Button> içinde <xref:System.Windows.Controls.StackPanel> bir <xref:System.Windows.Controls.StackPanel> işleyici tarafından `buttonContainer` <xref:System.Windows.FrameworkElement.Name%2A>ayarlanan örnek başvurusu aracılığıyla başvurur.

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Bir değişken gibi, bir örneğin XAML adı da bir kapsam kavramı tarafından yönetilir, böylece adlar öngörülebilir belirli bir kapsamda benzersiz olmaya zorlanabilir. Bir sayfayı tanımlayan birincil biçimlendirme, xaml adayır sınırı o sayfanın temel öğesi olmak üzere benzersiz bir XAML adayırını gösterir. Ancak, diğer biçimlendirme kaynakları, stiller veya stiller içindeki şablonlar gibi çalışma zamanında bir sayfayla etkileşim kurabilir ve bu tür biçimlendirme kaynaklarının genellikle sayfanın XAML adskopuyla bağlanmaması gereken kendi XAML adskopları vardır. Daha fazla `x:Name` bilgi ve XAML adskopları için bkz: <xref:System.Windows.FrameworkElement.Name%2A> [x:Ad Yönergesi](../xaml-services/xname-directive.md)veya [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Ekli özellikler ve ekli olaylar

XAML, belirli özelliklerin veya olayların, ayarlandığı öğeiçin tür tanımlarında özellik veya olayın var olup olmadığına bakılmaksızın, belirli özelliklerin veya olayların herhangi bir öğeüzerinde belirtilmesini sağlayan bir dil özelliği belirtir. Bu özelliğin özellikleri sürümü ekli özellik denir, olaylar sürümü ekli bir olay denir. Kavramsal olarak, ekli özellikleri ve ekli olayları herhangi bir XAML öğesi/nesne örneğinde ayarlanabilen global üyeler olarak düşünebilirsiniz. Ancak, bu öğe/sınıf veya daha büyük bir altyapı ekli değerler için bir destek özellik deposu desteklemesi gerekir.

XAML'deki ekli özellikler genellikle öznitelik sözdizimi ile kullanılır. Öznitelik sözdiziminde, formda `ownerType.propertyName`ekli bir özellik belirtirsiniz.

Yüzeysel olarak, bu bir özellik öğesi kullanımına benzer, ancak bu durumda `ownerType` belirttiğiniz öğe öğesi her zaman eklenmiş özelliğin ayarlandığı nesne öğesinden farklıdır. `ownerType`bir XAML işlemcitarafından eklenen özellik değerini almak veya ayarlamak için gereken erişimyöntemlerini sağlayan türdür.

Ekli özellikler için en yaygın senaryo, alt öğelerin bir özellik değerini üst öğelerine bildirmesini sağlamaktır.

Aşağıdaki örnekekli özelliği <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> göstermektedir. Sınıf, <xref:System.Windows.Controls.DockPanel> erişime girenleri <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> tanımlar ve bu nedenle ekli özelliğin sahibidir. Sınıf <xref:System.Windows.Controls.DockPanel> ayrıca alt öğelerini yineleyen ve özellikle her öğeyi 'nin <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>kümesini denetleyen mantık içerir. Bir değer bulunursa, bu değer düzen sırasında alt öğeleri konumlandırmak için kullanılır. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Ekli özelliğin kullanımı ve bu konumlandırma yeteneği aslında <xref:System.Windows.Controls.DockPanel> sınıf için motive edici senaryodur.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

WPF'de, ekli özelliklerin çoğu veya tümü bağımlılık özellikleri olarak da uygulanır. Daha fazla bilgi için [bkz.](../../framework/wpf/advanced/attached-properties-overview.md)

Ekli olaylar öznitelik `ownerType.eventName` sözdizimi benzer bir form kullanın. Ekli olmayan olaylar gibi, XAML'de ekli bir olayın öznitelik değeri, olay öğe üzerinde işlendiğinde çağrılan işleyici yönteminin adını belirtir. WPF XAML'deki ekli olay kullanımları daha az yaygındır. Daha fazla bilgi için bkz: [Ekteki Olaylara Genel Bakış.](../../framework/wpf/advanced/attached-events-overview.md)

## <a name="base-types-and-xaml"></a>Taban tipleri ve XAML

WPF XAML ve XAML ad alanının altında yatan, XAML için biçimlendirme öğelerine ek olarak CLR nesnelerine karşılık gelen türler topluluğudur. Ancak, tüm sınıflar öğelere eşlenebilir. CLR nesneleri <xref:System.Windows.Controls.Primitives.ButtonBase>modelinde devralma için ,, ve bazı soyut olmayan temel sınıflar gibi soyut sınıflar kullanılır. Soyut sınıflar da dahil olmak üzere temel sınıflar, somut XAML öğelerinin her biri kendi hiyerarşisinde bazı taban sınıftan üyeleri devraldığı için XAML gelişimi için hala önemlidir. Genellikle bu üyeler, öğe üzerinde öznitelik olarak ayarlanabilen özellikler veya işlenebilen olaylar içerir. <xref:System.Windows.FrameworkElement>WPF çerçeve düzeyinde WPF'nin somut temel UI sınıfıdır. UI tasarlarken, tüm türetmek çeşitli şekil, panel, dekoratör veya kontrol <xref:System.Windows.FrameworkElement>sınıfları, kullanır. İlgili bir taban <xref:System.Windows.FrameworkContentElement>sınıfı, api'leri kasıtlı olarak yansıtan API'leri kullanarak akış düzeni <xref:System.Windows.FrameworkElement>sunusu için iyi çalışan belge yönelimli öğeleri destekler. Öğe düzeyindeözler ve CLR nesne modeliözlerin birleşimi, belirli XAML öğesi ve altta yatan türüne bakılmaksızın, çoğu beton XAML öğesi üzerinde ayarlanan ortak özellikler kümesi sağlar.

## <a name="xaml-security"></a>XAML güvenliği

XAML, nesne anlık ve yürütmeyi doğrudan temsil eden bir biçimlendirme dilidir. Bu nedenle, XAML'de oluşturulan öğeler, sistem kaynaklarıyla (örneğin, dosya sistemi IO) eşdeğer oluşturulan kodla aynı etkileşim yeteneğine sahiptir. Tamamen güvenilir bir uygulamaya yüklenen XAML, barındırma uygulamasıyla aynı sistem kaynaklarına erişime sahiptir.

### <a name="code-access-security-cas-in-wpf"></a>WPF'de Kod Erişim Güvenliği (CAS)

**Bu bölüm yalnızca .NET Framework için geçerlidir. .NET Core için WPF CAS'ı desteklemez. Daha fazla bilgi için [Kod Erişim Güvenliği farklılıklarına](../migration/differences-from-net-framework.md#code-access-security)bakın.**

.NET Framework için WPF, Kod Erişim Güvenliği'ni (CAS) destekler. Bu, Internet bölgesinde çalışan WPF içeriğinin yürütme izinlerini azalttığı anlamına gelir. "Loose XAML" (bir XAML görüntüleyici tarafından yük zamanında yorumlanan derlenmeyen XAML sayfaları) ve XBAP genellikle bu internet bölgesinde çalıştırılır ve aynı izin kümesini kullanır. Ancak, tam olarak güvenilen bir uygulamaya yüklenen XAML, barındırma uygulamasıyla aynı sistem kaynaklarına erişime sahiptir. Daha fazla bilgi için [WPF Kısmi Güven Güvenliği'ne](../../framework/wpf/wpf-partial-trust-security.md)bakın.

## <a name="loading-xaml-from-code"></a>Koddan XAML yükleme

XAML, UI'nin tümünün tanımlanması için kullanılabilir, ancak bazen XAML'de UI'nin sadece bir parçasını tanımlamak da uygundur. Bu özellik, kısmi özelleştirmeyi, bilgilerin yerel depolanmasını, bir iş nesnesi sağlamak için XAML'yi veya çeşitli olası senaryoları etkinleştirmek için kullanılabilir. Bu senaryoların anahtarı <xref:System.Windows.Markup.XamlReader> sınıf ve <xref:System.Windows.Markup.XamlReader.Load%2A> yöntemidir. Giriş bir XAML dosyasıdır ve çıktı, bu biçimlendirmeden oluşturulan nesnelerin çalışma zamanı ağacının tümlerini temsil eden bir nesnedir. Daha sonra nesneyi uygulamada zaten var olan başka bir nesnenin özelliği olarak ekleyebilirsiniz. Özellik, nihai görüntüleme özelliklerine sahip içerik modelinde uygun bir özellik olduğu ve uygulama motoruna yeni içeriğin eklendiğini bildirdiği sürece, XAML'ye yükleyerek çalışan bir uygulamanın içeriğini kolayca değiştirebilirsiniz. .NET Framework için, bu özellik genellikle yalnızca tam güven uygulamalarında kullanılabilir, çünkü dosyaları çalışırken uygulamalara yüklemenin bariz güvenlik sonuçları ndan dolayı.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılı XAML Sözdizimi](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [WPF için XAML ve Özel Sınıflar](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [XAML Ad Alanı (x:) Dil Özellikleri](../xaml-services/namespace-language-features.md)
- [WPF XAML Uzantıları](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Temel Öğelere Genel Bakış](../../framework/wpf/advanced/base-elements-overview.md)
- [WPF İçinde Ağaçlar](../../framework/wpf/advanced/trees-in-wpf.md)
