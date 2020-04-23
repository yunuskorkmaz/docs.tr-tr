---
title: XAML'ye genel bakış
description: XAML dilinin .NET Core için Windows Presentation Foundation (WPF) tarafından nasıl yapılandırıldığını ve uygulandığını öğrenin.
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
# <a name="xaml-overview-in-wpf"></a>WPF 'de XAML 'ye Genel Bakış

Bu makalede XAML dilinin özellikleri açıklanmakta ve Windows Presentation Foundation (WPF) uygulamalarını yazmak için XAML 'yi nasıl kullanabileceğiniz gösterilmektedir. Bu makale, WPF tarafından uygulanan şekilde XAML 'yi tanımlar. XAML, WPF 'den daha büyük bir dil kavramıdır.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>XAML nedir?

XAML, bildirime dayalı bir biçimlendirme dilidir. .NET Core programlama modeli için uygulanan XAML, .NET Core uygulaması için bir kullanıcı arabirimi oluşturmayı basitleştirir. Bildirim temelli XAML biçimlendirmesinde görünür UI öğeleri oluşturabilir ve ardından, kısmi sınıf tanımları aracılığıyla biçimlendirmeye katılmış arka plan kod dosyalarını kullanarak, Kullanıcı arabirimi tanımını çalışma zamanı mantığından ayırabilirsiniz. XAML, derlemelerde tanımlanan belirli bir yedekleme türleri kümesindeki nesnelerin örneklenmesini doğrudan temsil eder. Bu, genellikle bir yedekleme türü sistemine doğrudan bir bağlama olmadan yorumlanan bir dil olan diğer birçok işaretleme dilinin aksine. XAML, farklı tarafların Kullanıcı arabiriminde ve bir uygulamanın mantığı üzerinde çalışabilmesine imkan tanıyan, potansiyel olarak farklı araçlar kullanan bir iş akışı sunar.

Metin olarak temsil edildiğinde, XAML dosyaları genellikle `.xaml` UZANTıSıNA sahip xml dosyalarıdır. Dosyalar herhangi bir XML kodlamasıyla kodlanabilir, ancak UTF-8 olarak kodlama tipik bir davranıştır.

Aşağıdaki örnek, bir kullanıcı arabiriminin parçası olarak nasıl bir düğme oluşturabileceğiniz gösterilmektedir. Bu örnek, XAML 'in ortak kullanıcı arabirimi programlama meta önem düzeyini nasıl temsil ettiğini belirten bir özellik sunmak için tasarlanmıştır (Bunun tamamı bir örnek değildir).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Kısaca XAML sözdizimi

Aşağıdaki bölümlerde, XAML sözdiziminin temel biçimleri açıklanacaktır ve kısa bir biçimlendirme örneği verilmiştir. Bu bölümler, her bir sözdizimi biçimi hakkında, bunların yedekleme türü sisteminde nasıl temsil edildiği gibi tüm bilgileri sağlamaya yönelik değildir. XAML sözdiziminin özellikleri hakkında daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

Sonraki birkaç bölümde bulunan malzemenin çoğu, XML diline daha önceden alışkın olmanız durumunda sizin için büyük olacaktır. Bu, XAML 'in temel tasarım ilkelerine bir sonucudur. XAML dili kendi kavramlarını tanımlar, ancak bu kavramlar XML dili ve biçimlendirme formu içinde çalışır.

### <a name="xaml-object-elements"></a>XAML nesne öğeleri

Bir nesne öğesi genellikle bir türün örneğini bildirir. Bu tür, XAML 'yi bir dil olarak kullanan teknoloji tarafından başvurulan derlemelerde tanımlanmıştır.

Nesne öğesi sözdizimi, her zaman bir sol açılı ayraç (`<`) ile başlar. Bunun ardından bir örnek oluşturmak istediğiniz türün adı gelir. (Ad, daha sonra açıklanacak bir kavram olan bir ön ek içerebilir.) Bundan sonra, isteğe bağlı olarak nesne öğesinde öznitelikler bildirebilirsiniz. Nesne öğesi etiketini doldurmak için, bir kapanış açılı ayracı (`>`) ile biter. Bunun yerine, eğik çizgiyle (`/>`) eğik çizgi ve kapanış açılı ayracı içeren etiketi tamamlayarak, herhangi bir içeriğe sahip olmayan bir kendi kendini kapatma formu kullanabilirsiniz. Örneğin, daha önce gösterilen biçimlendirme parçacığına tekrar bakın.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Bu iki nesne öğesini belirtir: `<StackPanel>` (içerik ve daha sonra bir kapatma etiketi) ve `<Button .../>` (birkaç özniteliği olan kendi kendini kapatma formu). Nesne öğeleri `StackPanel` ve `Button` her biri WPF tarafından tanımlanan bir SıNıFıN adına eşlenir ve WPF derlemelerinin bir parçasıdır. Bir nesne öğesi etiketi belirttiğinizde, temel alınan türün yeni bir örneğini oluşturmak için XAML işleme için bir yönerge oluşturursunuz. Her örnek, XAML ayrıştırılırken ve yüklenirken temeldeki türün parametresiz oluşturucusu çağırarak oluşturulur.

### <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (Özellikler)

Bir nesnenin özellikleri, genellikle nesne öğesinin öznitelikleri olarak ifade edilebilir. Öznitelik sözdizimi, ayarlanmakta olan Object özelliğini, ardından atama işleci (=) ile adlandırır. Bir özniteliğin değeri her zaman tırnak işaretleri içinde bulunan bir dize olarak belirtilir.

Öznitelik sözdizimi en kolay özellik ayarı sözdizimidir ve geçmişte biçimlendirme dillerini kullanan geliştiriciler için en sezgisel sözdizimidir. Örneğin, aşağıdaki biçimlendirme, olarak `Content`belirtilen görüntüleme metnine ek olarak kırmızı metin ve mavi bir arka plana sahip bir düğme oluşturur.

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Özellik öğesi sözdizimi

Bir nesne öğesinin bazı özellikleri için, özellik değeri sağlamak için gereken nesne veya bilgiler, öznitelik sözdiziminin tırnak işareti ve dize kısıtlamaları içinde yeterince ifade edilemediğinden öznitelik sözdizimi mümkün değildir. Bu gibi durumlarda, özellik öğesi sözdizimi olarak bilinen farklı bir sözdizimi kullanılabilir.

Özellik öğesi başlangıç etiketinin sözdizimi `<TypeName.PropertyName>`. Genellikle, bu etiketin içeriği özelliğin değeri olarak aldığı türün bir nesne öğesidir. İçeriği belirttikten sonra, özellik öğesini bir bitiş etiketiyle kapatmanız gerekir. Bitiş etiketinin sözdizimi `</TypeName.PropertyName>`.

Bir öznitelik sözdizimi mümkünse, öznitelik söz dizimini kullanmak genellikle daha kolay olur ve daha küçük bir biçimlendirme sunar, ancak bu genellikle bir stil, teknik bir kısıtlama değildir. Aşağıdaki örnek, önceki öznitelik sözdizimi örneğinde olduğu gibi ayarlanan özelliklerin aynısını gösterir, ancak bu kez öğesinin tüm özellikleri için özellik öğesi söz dizimi kullanılarak `Button`.

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Koleksiyon sözdizimi

XAML dili, daha fazla insan tarafından okunabilen biçimlendirme üreten bazı iyileştirmeler içerir. Bu tür iyileştirmede, belirli bir özellik bir koleksiyon türü alırsa, biçimlendirmede tanımladığınız öğelerin, bu özelliğin değeri içindeki alt öğe olarak, koleksiyonun bir parçası haline gelir. Bu durumda, alt nesne öğelerinin bir koleksiyonu koleksiyon özelliğine ayarlanmakta olan değerdir.

Aşağıdaki örnek, <xref:System.Windows.Media.GradientBrush.GradientStops%2A> özelliğinin değerlerini ayarlamak için koleksiyon sözdizimini gösterir.

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

XAML, bir sınıfın özelliklerinden tam olarak birini XAML _içerik_ özelliği olacak şekilde belirleyebildiği bir dil özelliğini belirtir. Bu nesne öğesinin alt öğeleri, bu içerik özelliğinin değerini ayarlamak için kullanılır. Diğer bir deyişle, içerik özelliği benzersiz bir şekilde, XAML biçimlendirmesinde bu özelliği ayarlarken ve daha görünür bir üst/alt metaphı veya biçimlendirme içinde bir özellik öğesini atlayabilirsiniz.

Örneğin, <xref:System.Windows.Controls.Border> öğesinin <xref:System.Windows.Controls.Decorator.Child%2A>bir _içerik_ özelliğini belirtir. Aşağıdaki iki <xref:System.Windows.Controls.Border> öğe aynı şekilde ele alınır. Birincisi, içerik özelliği sözdiziminden yararlanır ve `Border.Child` özellik öğesini atlar. İkinci bir, açıkça `Border.Child` gösterir.

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

XAML dilinin bir kuralı olarak, XAML içerik özelliğinin değeri, nesne öğesindeki diğer herhangi bir özellik öğesinden tamamen önce veya tamamen bir değere verilmelidir. Örneğin, aşağıdaki biçimlendirme derlenemiyor.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

XAML sözdiziminin özellikleri hakkında daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Metin içeriği

Küçük sayıda XAML öğesi, metni içerik olarak doğrudan işleyebilir. Bunu etkinleştirmek için aşağıdaki durumlardan biri doğru olmalıdır:

- Sınıf bir içerik özelliği bildirmelidir ve bu içerik özelliği bir dizeye atanabilir türde olmalıdır (tür olabilir <xref:System.Object>). Örneğin, herhangi biri <xref:System.Windows.Controls.ContentControl> içerik <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği olarak, ve <xref:System.Object>türü olarak kullanılır ve bu, aşağıdaki kullanımı <xref:System.Windows.Controls.ContentControl> bir <xref:System.Windows.Controls.Button>gibi destekler:. `<Button>Hello</Button>`

- Tür bir tür dönüştürücüsü bildirmelidir, bu durumda metin içeriği bu tür Dönüştürücüsü için başlatma metni olarak kullanılır. Örneğin, `<Brush>Blue</Brush>` öğesinin `Blue` içerik değerini bir fırçaya dönüştürür. Bu durum, uygulamada daha az yaygındır.

- Tür, bilinen bir XAML dil temel türü olmalıdır.

### <a name="content-properties-and-collection-syntax-combined"></a>İçerik özellikleri ve koleksiyon sözdizimi birleştirildi

Bu örneği göz önünde bulundurun.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Burada her biri <xref:System.Windows.Controls.Button> bir alt öğesidir <xref:System.Windows.Controls.StackPanel>. Bu, iki farklı nedenden dolayı iki etiketi atlamayan kolaylaştırılmış ve sezgisel bir işaretlemedir.

- **Atlanan StackPanel. Children Özellik öğesi:** <xref:System.Windows.Controls.StackPanel> öğesinden <xref:System.Windows.Controls.Panel>türetilir. <xref:System.Windows.Controls.Panel>XAML <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> içerik özelliği olarak tanımlar.

- **Atlanan UIElementCollection nesne öğesi:** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> Özelliği, öğesini uygulayan <xref:System.Collections.IList>türünü <xref:System.Windows.Controls.UIElementCollection>alır. Koleksiyonun element etiketi, gibi koleksiyonları işlemek için XAML kurallarına göre atlanabilir <xref:System.Collections.IList>. (Bu durumda, <xref:System.Windows.Controls.UIElementCollection> parametresiz bir Oluşturucu sunmadığından ve <xref:System.Windows.Controls.UIElementCollection> nesne öğesi açıklama olarak gösterilmekte olduğundan, aslında örnek oluşturulamıyor).

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

Öznitelik sözdizimi Ayrıca, özellikler yerine olaylar olan üyeler için de kullanılabilir. Bu durumda, özniteliğin adı olayın adıdır. XAML için olaylar WPF uygulamasında özniteliğin değeri, bu olayın temsilcisini uygulayan işleyicinin adıdır. Örneğin, aşağıdaki biçimlendirme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay <xref:System.Windows.Controls.Button> için bir işleyiciyi bir tanıtıcı olarak atar:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

Bu öznitelik sözdiziminin yalnızca bu örneğinde, WPF 'de daha fazla olay ve XAML vardır. Örneğin, burada `ClickHandler` başvurulan ' nin ne olduğunu ve nasıl tanımlandığını merak ediyor olabilirsiniz. Bu, bu makalenin yaklaşan [Olaylar ve xaml arka plan kod](#events-and-xaml-code-behind) bölümünde açıklanmaktadır.

## <a name="case-and-white-space-in-xaml"></a>XAML 'de Case ve boşluk

Genel olarak, XAML büyük/küçük harfe duyarlıdır. Yedekleme türlerinin çözümlenmesi amacıyla WPF XAML, CLR 'nin büyük/küçük harfe duyarlı olduğu kurallarla büyük/küçük harfe duyarlıdır. Nesne öğeleri, özellik öğeleri ve öznitelik adları, derleme içindeki temel alınan türe veya bir tür üyesine göre karşılaştırıldığında duyarlı büyük küçük harf kullanılarak belirtilmelidir. XAML dil anahtar sözcükleri ve temel elemanlar Ayrıca büyük/küçük harfe duyarlıdır. Değerler her zaman büyük/küçük harfe duyarlı değildir. Değerler için büyük/küçük harf duyarlılığı, değeri alan özellikle ilişkili tür dönüştürücüsü davranışına veya özellik değeri türüne bağlıdır. Örneğin, <xref:System.Boolean> türü alan özellikler yalnızca eşdeğer değerler `true` `True` olarak alabilir, ancak yalnızca dize <xref:System.Boolean> için yerel WPF XAML ayrıştırıcısı tür dönüştürmesi bu şekilde eşdeğerleri olarak izin veriyor.

WPF XAML işlemcileri ve serileştiriciler, tüm önemli olmayan boşlukları yoksayacak veya bırakacak ve tüm önemli boşlukları normalleştirilecektir. Bu, XAML belirtiminin varsayılan beyaz boşluk davranışı önerileri ile tutarlıdır. Bu davranış yalnızca XAML içerik özellikleri içinde dizeler belirttiğinizde ortaya bir sonucudur. En basit koşullarda, XAML boşluk, linefeed ve sekme karakterlerini boşluklara dönüştürür ve sonra bitişik bir dizenin herhangi bir ucunda bulunursa bir boşluk korur. XAML beyaz alanı işlemenin tam açıklaması bu makalede ele alınmıyor. Daha fazla bilgi için bkz. [xaml 'de beyaz boşluk işleme](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>İşaretleme uzantıları

Biçimlendirme uzantıları bir XAML dil kavramıdır. Bir öznitelik sözdizimi değeri sağlamak için kullanıldığında, küme ayraçları (`{` ve `}`) biçimlendirme uzantısı kullanımını gösterir. Bu kullanım, XAML işlemesini, bir sabit dize veya dize dönüştürülebilir bir değer olarak öznitelik değerlerinin genel işlemeden çıkmak için yönlendirir.

WPF uygulama programlamasında [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)kullanılan en yaygın biçimlendirme uzantıları, veri bağlama ifadeleri ve kaynak başvuruları [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) için kullanılır. [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md) Biçimlendirme uzantıları ' nı kullanarak, bu özellik genel olarak bir öznitelik sözdizimini desteklemeseler bile özellikler için değerler sağlamak üzere öznitelik sözdizimini kullanabilirsiniz. Biçimlendirme uzantıları genellikle değerleri erteleme veya çalışma zamanında bulunan diğer nesnelere başvurma gibi özellikleri etkinleştirmek için ara ifade türlerini kullanır.

Örneğin, aşağıdaki biçimlendirme öznitelik söz dizimini kullanarak <xref:System.Windows.FrameworkElement.Style%2A> özelliğin değerini ayarlar. <xref:System.Windows.FrameworkElement.Style%2A> Özelliği, <xref:System.Windows.Style> sınıfının bir örneğini alır ve bu, varsayılan olarak bir öznitelik sözdizimi dizesi tarafından örneklenemez. Ancak bu durumda öznitelik belirli bir biçimlendirme uzantısına başvurur `StaticResource`. Biçimlendirme Uzantısı işlendiğinde, daha önce kaynak sözlüğünde anahtarlı kaynak olarak örneklenen bir stile başvuru döndürür.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Özellikle WPF 'de uygulanan XAML için tüm biçimlendirme uzantılarının başvuru listesi için bkz. [WPF XAML uzantıları](../../framework/wpf/advanced/wpf-xaml-extensions.md). System. xaml tarafından tanımlanan ve .NET Core XAML uygulamalarında daha yaygın olarak kullanılabilen biçimlendirme uzantılarının başvuru listesi için bkz. [xaml ad alanı (x:) Dil özellikleri](../xaml-services/namespace-language-features.md). Biçimlendirme Uzantısı kavramları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Tür dönüştürücüler

[Kısaca xaml sözdiziminde](#xaml-syntax-in-brief) , öznitelik değeri bir dize tarafından ayarlanamayacak şekilde belirtilmiştir. Dizelerin diğer nesne türlerine nasıl dönüştürüldüğüne ilişkin temel, yerel işleme, <xref:System.String> <xref:System.DateTime> veya <xref:System.Uri>gibi belirli türler için yerel işlemeye ek olarak türün kendisini temel alır. Ancak bu türlerin birçok WPF türü veya üyesi, temel dize özniteliği işleme davranışını daha karmaşık nesne türleri örneklerinin dizeler ve öznitelikler olarak belirtilebilmesi için genişletir.

<xref:System.Windows.Thickness> Yapı, XAML kullanımları için etkinleştirilmiş tür dönüştürmesi olan bir türün örneğidir. <xref:System.Windows.Thickness>iç içe yerleştirilmiş bir dikdörtgen içindeki ölçüleri gösterir ve gibi özellikler için değer olarak kullanılır <xref:System.Windows.FrameworkElement.Margin%2A>. Üzerine <xref:System.Windows.Thickness>bir tür dönüştürücüsü yerleştirerek, ' ı kullanan <xref:System.Windows.Thickness> tüm özelliklerin xaml 'de belirtilmesi daha kolaydır çünkü bunlar öznitelik olarak belirtibilirler. Aşağıdaki örnek, bir <xref:System.Windows.FrameworkElement.Margin%2A>için değer sağlamak üzere bir tür dönüştürme ve öznitelik söz dizimini kullanır:

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

Önceki öznitelik sözdizimi örneği aşağıdaki daha ayrıntılı sözdizimi örneğine eşdeğerdir; burada <xref:System.Windows.FrameworkElement.Margin%2A> bunun yerine, <xref:System.Windows.Thickness> nesne öğesi içeren özellik öğesi söz dizimi aracılığıyla ayarlanır. Öğesinin <xref:System.Windows.Thickness> dört anahtar özelliği, yeni örnekte öznitelikler olarak ayarlanır:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Ayrıca, türün kendisi parametresiz bir oluşturucuya sahip olmadığı için, tür dönüştürmenin bir alt sınıf eklemeden bu türe bir özelliği ayarlamaya yönelik tek ortak yol olduğu sınırlı sayıda nesne vardır. <xref:System.Windows.Input.Cursor> bunun bir örneğidir.

Tür dönüştürmesi hakkında daha fazla bilgi için bkz. [TypeConverters ve xaml](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML kök öğeleri ve XAML ad alanları

Bir XAML dosyasının hem iyi biçimlendirilmiş bir XML dosyası hem de geçerli bir XAML dosyası olması için yalnızca bir kök öğesi olmalıdır. Tipik WPF senaryolarında, WPF uygulama modelinde anlamlı bir anlamı olan bir kök öğe kullanırsınız (örneğin <xref:System.Windows.Window> , veya <xref:System.Windows.Controls.Page> bir sayfa <xref:System.Windows.ResourceDictionary> için, bir dış sözlük için ya <xref:System.Windows.Application> da uygulama tanımı için). Aşağıdaki örnek, bir WPF sayfası için tipik bir XAML dosyasının kök öğesi olan kök öğesini gösterir <xref:System.Windows.Controls.Page>.

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

Kök öğe ayrıca özniteliklerini `xmlns` ve `xmlns:x`içerir. Bu öznitelikler, xaml ad alanlarının, biçimlendirmenin öğe olarak başvurabileceği türleri desteklemek için tür tanımlarını içerdiği XAML işlemcisine işaret eder. `xmlns` Özniteliği özellıkle varsayılan xaml ad alanını gösterir. Varsayılan XAML ad alanı içinde, biçimlendirme içindeki nesne öğeleri ön ek olmadan belirlenebilir. Çoğu WPF uygulama senaryosu ve SDK 'nın WPF bölümlerinde verilen örneklerin neredeyse hepsi için, varsayılan XAML ad alanı WPF ad alanına `http://schemas.microsoft.com/winfx/2006/xaml/presentation`eşlenir. `xmlns:x` ÖZNITELIK, XAML dili ad alanını `http://schemas.microsoft.com/winfx/2006/xaml`eşleyen ek xaml ad alanını gösterir.

Bir NameScope `xmlns` 'un kullanım ve eşleme kapsamını tanımlamak için bu kullanımı, XML 1,0 belirtimiyle tutarlıdır. Xaml ad kapsamları yalnızca XML ad kapsamları 'den farklıdır, ancak xaml namescope yalnızca, ad çözümleme ve xaml ayrıştırmaya geldiğinde NameScope öğelerinin türler tarafından nasıl desteklendiği hakkında bir şeyi de gösterir.

Öznitelikler `xmlns` , her xaml dosyasının kök öğesinde yalnızca kesinlikle gereklidir. `xmlns`tanımlar, kök öğenin tüm alt öğelerine uygulanır (Bu davranış, için `xmlns`XML 1,0 belirtimiyle birlikte yeniden tutarlıdır.) `xmlns` öznitelikleri kök altındaki diğer öğelerde de izin verilir ve tanımlayan öğenin tüm alt öğelerine uygulanır. Ancak XAML ad alanlarının sık tanım veya yeniden tanımlanması, okunması zor olan XAML biçimlendirme stiline neden olabilir.

XAML işlemcisinin WPF uygulamasında WPF çekirdek derlemelerinin farkında olan bir altyapı bulunur. WPF çekirdek derlemelerinin, varsayılan XAML ad alanı için WPF eşlemelerini destekleyen türleri içermesi bilinmektedir. Bu, proje derleme dosyanızın ve WPF yapı ve proje sistemlerinin bir parçası olan yapılandırma aracılığıyla etkinleştirilir. Bu nedenle, varsayılan XAML ad alanını varsayılan `xmlns` olarak BILDIRMEK, WPF DERLEMELERINDEN gelen xaml öğelerine başvurmak için gereklidir.

### <a name="the-x-prefix"></a>X: ön eki

Önceki kök öğe örneğinde, önek `x:` xaml ad alanını `http://schemas.microsoft.com/winfx/2006/xaml`EŞLEMEK için kullanıldı, XAML DIL yapılarını destekleyen ayrılmış xaml ad alanı. Bu `x:` ön ek, bu xaml ad alanını projeler için şablonlarda, örneklerde ve bu SDK 'nın tamamında belgelerde eşlemek için kullanılır. Xaml dilinin XAML ad alanı, XAML 'unuzda sık kullanacağınız çeşitli programlama yapıları içerir. Aşağıda, kullanacağınız en yaygın `x:` önek programlama yapılarının bir listesi verilmiştir:

- [x:Key](../xaml-services/xkey-directive.md): (veya diğer çerçevelerde benzer bir <xref:System.Windows.ResourceDictionary> sözlük kavramlarından) her kaynak için benzersiz bir anahtar ayarlar. `x:Key`tipik bir WPF uygulamasının biçimlendirmesinde göreceğiniz `x:` kullanımların yüzde 90 ' ünü hesaba atayacaksınız.

- [X:Class](../xaml-services/xclass-directive.md): XAML sayfası için arka plan kodu sağlayan sınıf için clr ad alanını ve sınıf adını belirtir. WPF programlama modeli başına arka plan kodunu desteklemek için böyle bir sınıfa sahip olmanız gerekir. bu nedenle, hiç kaynak olmasa bile `x:` neredeyse her zaman eşleştirilmiş olarak görürsünüz.

- [X:Name](../xaml-services/xname-directive.md): bir nesne öğesi işlendikten sonra çalışma zamanı kodunda bulunan örnek için bir çalışma zamanı nesne adı belirtir. Genel olarak, [X:Name](../xaml-services/xname-directive.md)IÇIN genellikle WPF tanımlı eşdeğer bir özellik kullanacaksınız. Bu tür özellikler özellikle bir CLR yedekleme özelliğine eşlenir ve bu nedenle, başlatılan XAML 'den adlandırılmış öğeleri bulmak için sıklıkla çalışma zamanı kodunu kullandığınız uygulama programlaması için daha uygundur. En yaygın olarak <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>kullanılan özellik. Aynı WPF çerçevesi düzeyi <xref:System.Windows.FrameworkElement.Name%2A> özelliği belirli bir türde desteklenmediğinden, [x:Name](../xaml-services/xname-directive.md) kullanmaya devam edebilirsiniz. Bu, belirli animasyon senaryolarında meydana gelir.

- [X:static](../xaml-services/xstatic-markup-extension.md): başka türlü xaml uyumlu özelliği olmayan statik bir değer döndüren başvuruyu verir.

- [x:Type](../xaml-services/xtype-markup-extension.md): bir tür <xref:System.Type> adını temel alan bir başvuru oluşturur. Bu, genellikle özelliğinin, [X:Type](../xaml-services/xtype-markup-extension.md) işaretleme <xref:System.Type>uzantısı kullanımının isteğe <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>bağlı olduğu şekilde yerel olarak<xref:System.Type> dönüştürülmesine sahip olmasına rağmen, gibi öznitelikleri belirtmek için kullanılır.

`x:` Önek/xaml ad alanında, ortak olmayan ek programlama yapıları vardır. Ayrıntılar için bkz. [xaml ad alanı (x:) Dil özellikleri](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML 'de özel ön ekler ve özel türler

Kendi özel derlemeleriniz veya **PresentationCore**, **PresentationFramework** ve **WindowsBase**'in WPF çekirdeği dışındaki derlemeler için, derlemeyi özel `xmlns` eşlemenin bir parçası olarak belirtebilirsiniz. Daha sonra XAML içindeki bu derlemeden türlere başvurabilirsiniz, bu nedenle bu tür, denediğiniz XAML kullanımlarını destekleyecek şekilde doğru şekilde uygulanır.

Özel ön eklerin XAML biçimlendirmesinde nasıl çalıştığı hakkında temel bir örnek aşağıda verilmiştir. Ön ek `custom` , kök öğe etiketinde tanımlanmıştır ve paketlenmiş ve uygulamayla kullanılabilir olan belirli bir derlemeyle eşleştirilir. Bu derleme, genel XAML `NumericUpDown`kullanımını desteklemek için uygulanan ve bır WPF XAML içerik modelinde bu belirli noktada eklenmesine izin veren bir sınıf devralma kullanan bir tür içerir. Bu `NumericUpDown` denetimin bir örneği, bir XAML ayrıştırıcısı türü hangi xaml ad alanının içerdiğini bilmesi ve bu nedenle, yedekleme derlemesinin tür tanımını içermesi halinde öneki kullanılarak nesne öğesi olarak bildirilmiştir.

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

XAML 'deki özel türler hakkında daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

Derlemelerdeki XML ad alanları ve kod ad alanları hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Olaylar ve XAML arka plan kodu

Çoğu WPF uygulaması hem XAML biçimlendirmesi hem de arka plan kodundan oluşur. Bir proje içinde, XAML bir `.xaml` dosya olarak yazılır ve bir arka plan kod dosyası yazmak için Microsoft Visual Basic veya C# gıbı bir clr dili kullanılır. Bir XAML dosyası WPF programlama ve uygulama modellerinin bir parçası olarak derlendiğinde, xaml dosyası için XAML arka plan kod dosyasının konumu, XAML kök öğesinin `x:Class` özniteliği olarak bir ad alanı ve sınıf belirtilerek tanımlanır.

Şu ana kadar örnek olarak birkaç düğme gördünüz, ancak bu düğmelerden hiçbiri henüz bunlarla ilişkili herhangi bir mantıksal davranışa sahip değil. Bir nesne öğesi için bir davranış eklemeye yönelik birincil uygulama düzeyi mekanizması, öğe sınıfının var olan bir olayını kullanmak ve bu olay çalışma zamanında oluşturulduğunda çağrılan bu olay için belirli bir işleyici yazmak içindir. Olay adı ve kullanılacak işleyicinin adı, biçimlendirmede belirtilir, ancak işleyicinizi uygulayan kod, arka plan kod içinde tanımlanır.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Arka plan kod dosyasının CLR ad `ExampleNamespace` alanını kullandığını ve bu ad alanı içinde `ExamplePage` kısmi bir sınıf olarak bildirdiğine dikkat edin. Bu, `x:Class` öğesinin `ExampleNamespace`öznitelik değerini paraleldir.`ExamplePage` Bu, biçimlendirme kökünde verilmiştir. WPF biçimlendirme derleyicisi, kök öğe türünden bir sınıf türeterek, derlenmiş XAML dosyaları için kısmi bir sınıf oluşturur. Aynı kısmi sınıfı da tanımlayan arka plan kodu sağladığınızda, elde edilen kod derlenen uygulamanın aynı ad alanı ve sınıfı içinde birleştirilir.

WPF 'deki arka plan kod programlamaya yönelik gereksinimler hakkında daha fazla bilgi için bkz. [WPF 'de kod arkasındaki, olay işleyicisi ve kısmi sınıf gereksinimleri](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf).

Ayrı bir arka plan kod dosyası oluşturmak istemiyorsanız, kodunuzu bir XAML dosyasında da satır içinde oluşturabilirsiniz. Ancak, satır içi kod önemli sınırlamalara sahip daha az yönlü bir tekniktir. Daha fazla bilgi için bkz. [WPF Içinde arka plan kodu ve xaml](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

### <a name="routed-events"></a>Yönlendirilmiş olaylar

WPF için temel olan belirli bir olay özelliği, yönlendirilmiş bir olaydır. Yönlendirilmiş olaylar, öğe bir ağaç ilişkisiyle bağlandığı sürece, farklı bir öğe tarafından oluşturulan bir olayı işlemesini sağlar. Bir XAML özniteliğiyle olay işleme belirtirken, yönlendirilmiş olay, sınıf üyeleri tablosunda söz konusu olayı listelemeyen öğeler de dahil olmak üzere herhangi bir öğede listenilir ve işlenebilir. Bu, sahip sınıf adıyla olay adı özniteliği niteleyerek gerçekleştirilir. Örneğin `StackPanel` , devam eden `StackPanel`  /  `Button` örnekteki üst öğe, öznitelik değeri olarak işleyici adınızla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> `Button.Click` `StackPanel` nesne öğesinde özniteliğini belirterek alt öğe düğmesinin olayı için bir işleyici kaydedebilir. Daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>XAML adlandırılmış öğeleri

Varsayılan olarak, bir XAML nesne öğesi işlenerek bir nesne grafiğinde oluşturulan nesne örneği, benzersiz bir tanımlayıcıya veya nesne başvurusuna sahip değildir. Buna karşılık, kodda bir Oluşturucu çağırırsanız, daha sonra kodunuzda daha sonra başvuruda bulunmak için, Oluşturucu sonucunu neredeyse her zaman oluşturulan örneğe bir değişken ayarlamak üzere kullanacaksınız. Bir biçimlendirme tanımı aracılığıyla oluşturulmuş nesnelere standartlaştırılmış erişim sağlamak için XAML, [X:Name özniteliğini](../xaml-services/xname-directive.md)tanımlar. `x:Name` Özniteliğin değerini herhangi bir nesne öğesinde ayarlayabilirsiniz. Arka plan kodunuzda, seçtiğiniz tanımlayıcı oluşturulan örneğe başvuran bir örnek değişkenine eşdeğerdir. Tüm durumlarda, adlandırılmış öğeler nesne örneklermiş gibi işlev görür (ad bu örneğe başvurur) ve arka plan kodunuz, uygulama içindeki çalışma zamanı etkileşimlerini işlemek için adlandırılmış öğelere başvurabilir. Örnekler ve değişkenler arasındaki bu bağlantı WPF XAML biçimlendirme derleyicisi tarafından gerçekleştirilir ve daha fazla özellikle, bu makalede ayrıntılı olarak açıklanmayacak gibi <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> özellikleri ve desenleri içerir.

WPF Framework-Level XAML öğeleri, XAML <xref:System.Windows.FrameworkElement.Name%2A> tanımlı `x:Name` özniteliğine denk gelen bir özelliği devralınır. Ayrıca, bazı diğer sınıflar için `x:Name`Özellik düzeyi eşdeğerleri da sağlar, bu da genellikle `Name` özellik olarak tanımlanır. Genellikle, seçili öğe/tür için Üyeler `Name` tablosunda bir özellik bulamazsanız, bunun yerine kullanın `x:Name` . `x:Name` Değerler, belirli alt sistemler veya gibi <xref:System.Windows.FrameworkElement.FindName%2A>yardımcı yöntemler tarafından, çalışma zamanında kullanılabilecek bir xaml öğesine bir tanımlayıcı sağlar.

Aşağıdaki örnek bir <xref:System.Windows.Controls.StackPanel> öğesi <xref:System.Windows.FrameworkElement.Name%2A> üzerinde ayarlanır. <xref:System.Windows.Controls.Button> Ardından, içindeki bir işleyicisi, tarafından <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.StackPanel> `buttonContainer` <xref:System.Windows.FrameworkElement.Name%2A>ayarlanan örnek başvurusu aracılığıyla başvuruda bulunan bir işleyici.

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Bir değişken gibi, bir örnek için XAML adı bir kapsam kavramıyla yönetilir, böylece adların öngörülebilir olan belirli bir kapsam içinde benzersiz olmasını zorunlu hale getirebilirsiniz. Bir sayfayı tanımlayan birincil biçimlendirme, XAML namescope sınırının bu sayfanın kök öğesi olduğu benzersiz bir XAML namescope olduğunu gösterir. Bununla birlikte, diğer biçimlendirme kaynakları, çalışma zamanında bir sayfayla etkileşime geçebilir (Stiller ve stiller içindeki şablonlar gibi) ve bu biçimlendirme kaynakları genellikle sayfanın XAML namescope 'a bağlanmayan kendi XAML nameslerini kullanır. `x:Name` Ve xaml namescopes hakkında daha fazla bilgi için bkz <xref:System.Windows.FrameworkElement.Name%2A>., [x:Name Yönergesi](../xaml-services/xname-directive.md)veya [WPF xaml namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Ekli Özellikler ve ekli olaylar

XAML, özelliğin veya olayın, üzerinde ayarlandığı öğe için tür tanımlarında bulunup olmamasından bağımsız olarak, belirli özelliklerin veya olayların herhangi bir öğede belirtilmesini sağlayan bir dil özelliğini belirtir. Bu özelliğin Özellikler sürümüne iliştirilmiş bir özellik denir, olaylar sürümüne ekli olay denir. Kavramsal olarak, ekli özellikleri ve ekli olayları herhangi bir XAML öğesi/nesne örneği üzerinde ayarlayalebilecek Genel Üyeler olarak düşünebilirsiniz. Ancak, bu öğe/sınıf veya daha büyük bir altyapı, ekli değerler için bir yedekleme özelliği deposu desteklemelidir.

XAML 'deki Ekli özellikler genellikle öznitelik söz dizimi aracılığıyla kullanılır. Öznitelik sözdiziminde, formda `ownerType.propertyName`iliştirilmiş bir özellik belirtirsiniz.

Bu, bir özellik öğesi kullanımına benzer, ancak bu durumda `ownerType` belirttiğiniz her zaman, iliştirilmiş özelliğin ayarlandığı nesne öğesinden farklı bir tür. `ownerType`, iliştirilmiş özellik değerini almak veya ayarlamak için XAML işlemcisi tarafından gerekli olan erişimci yöntemlerini sağlayan türdür.

Ekli Özellikler için en yaygın senaryo, alt öğelerin bir özellik değerini üst öğelerine raporlamalarını olanaklı hale etkinleştirmektir.

Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özelliği gösterir. <xref:System.Windows.Controls.DockPanel> Sınıfı, için <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> erişimcileri tanımlar ve bu nedenle iliştirilmiş özelliğine sahip olur. <xref:System.Windows.Controls.DockPanel> Sınıfı ayrıca, alt öğelerini yineleyen ve küme değeri için her öğeyi özel olarak denetleyen mantığı da içerir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Bir değer bulunursa, alt öğeleri konumlandırmak için Düzen sırasında bu değer kullanılır. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Eklenmiş özelliğin kullanımı ve bu konumlandırma özelliği, <xref:System.Windows.Controls.DockPanel> sınıf için bir mücadele senaryosuna yöneliktir.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

WPF 'de, eklenen özelliklerin çoğu veya tümü bağımlılık özellikleri olarak da uygulanır. Daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../../framework/wpf/advanced/attached-properties-overview.md).

Ekli olaylar, öznitelik söz `ownerType.eventName` dizimini benzer bir biçimde kullanır. Eklenmemiş olaylara benzer şekilde, XAML 'de ekli bir olayın öznitelik değeri, olay öğesinde işlendiği zaman çağrılan işleyici yönteminin adını belirtir. WPF XAML 'de ekli olay kullanımları daha az yaygındır. Daha fazla bilgi için bkz. [ekli olaylara genel bakış](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Temel türler ve XAML

Temel alınan WPF XAML ve XAML ad alanı, XAML için biçimlendirme öğelerine ek olarak CLR nesnelerine karşılık gelen türlerin bir koleksiyonudur. Ancak, tüm sınıflar öğelerle eşleştirilemez. , Ve gibi <xref:System.Windows.Controls.Primitives.ButtonBase>soyut olmayan taban SıNıFLAR, CLR nesneleri modelinde devralma için kullanılır. Soyut olanlar dahil temel sınıflar, XAML geliştirmesi için hala önemlidir çünkü somut XAML öğelerinin her biri hiyerarşideki bazı temel sınıflardan üyeleri devralır. Genellikle bu Üyeler öğe üzerinde öznitelik olarak ayarlanabilir özellikleri veya işlenebilen olayları içerir. <xref:System.Windows.FrameworkElement>WPF 'in, WPF çerçeve düzeyindeki somut temel kullanıcı arabirimi sınıfıdır. Kullanıcı arabirimi tasarlarken, hepsi ' den <xref:System.Windows.FrameworkElement>türetilen çeşitli şekil, panel, dekoratörü veya denetim sınıflarını kullanırsınız. <xref:System.Windows.FrameworkContentElement>İle ilgili temel sınıf, Içindeki <xref:System.Windows.FrameworkElement>API 'Leri kasıtlı olarak yansıtan API 'leri kullanarak bir akış düzeni sunumunda iyi çalışan belge yönelimli öğeleri destekler. Öğe düzeyinde özniteliklerin birleşimi ve bir CLR nesne modeli, belirli XAML öğesi ve temel alınan türü ne olursa olsun, en somut XAML öğelerine ayarlanabilir ortak özellikler kümesi sağlar.

## <a name="xaml-security"></a>XAML güvenliği

XAML doğrudan nesne örneğini oluşturma ve yürütmeyi temsil eden bir biçimlendirme dilidir. Bu nedenle, XAML 'de oluşturulan öğelerin, sistem kaynaklarıyla etkileşim kurma özelliği (örneğin, ağ erişimi, dosya sistemi GÇ dosyası), eşdeğer oluşturulan kod olarak aynıdır. Tam güvenilir bir uygulamaya yüklenen XAML, barındırma uygulaması tarafından sistem kaynaklarına aynı erişime sahiptir.

### <a name="code-access-security-cas-in-wpf"></a>WPF 'de kod erişim güvenliği (CAS)

**Bu bölüm yalnızca .NET Framework için geçerlidir. .NET Core için WPF, CA 'ları desteklemez. Daha fazla bilgi için bkz. [kod erişimi güvenlik farklılıkları](../migration/differences-from-net-framework.md#code-access-security).**

.NET Framework için WPF, kod erişim güvenliğini (CAS) destekler. Bu, Internet bölgesinde çalışan WPF içeriğinin yürütme izinlerinin azaldığı anlamına gelir. "Gevşek XAML" (bir XAML Görüntüleyicisi tarafından yükleme sırasında yorumlanan derlenmiş XAML sayfaları) ve XBAP genellikle bu Internet bölgesinde çalışır ve aynı izin kümesini kullanır. Ancak, tam güvenilir bir uygulamaya yüklenen XAML, barındırma uygulaması tarafından sistem kaynaklarına aynı erişime sahiptir. Daha fazla bilgi için bkz. [WPF Kısmi güven güvenliği](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Koddan XAML yükleme

XAML, tüm Kullanıcı arabirimini tanımlamak için kullanılabilir, ancak bazen XAML 'de UI 'nin bir parçasını tanımlamak için de uygundur. Bu özellik Kısmi özelleştirmeyi, bilgi yerel depolamayı, bir iş nesnesi sağlamak için XAML kullanmayı veya çeşitli olası senaryoları etkinleştirmek için kullanılabilir. Bu senaryolara yönelik anahtar, <xref:System.Windows.Markup.XamlReader> sınıfı ve <xref:System.Windows.Markup.XamlReader.Load%2A> yöntemidir. Giriş bir XAML dosyasıdır ve çıktı, bu işaretten oluşturulan nesnelerin çalışma zamanı ağacını temsil eden bir nesnedir. Daha sonra nesneyi, uygulamada zaten var olan başka bir nesnenin özelliği olacak şekilde ekleyebilirsiniz. Özelliği, içerik modelinde son görüntüleme özelliklerine sahip uygun bir özellik olduğu ve yürütme altyapısını uygulamaya yeni içerik eklendiğini bildirecek şekilde, çalışan bir uygulamanın içeriğini XAML 'e yükleyerek kolayca değiştirebilirsiniz. .NET Framework için, bu özellik genellikle yalnızca tam güven uygulamalarında kullanılabilir. Bu özellik, dosyaları çalıştıkları şekilde uygulamalara yüklemenin belirgin güvenlik etkilerine yöneliktir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılı XAML Sözdizimi](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [WPF için XAML ve Özel Sınıflar](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [XAML Ad Alanı (x:) Dil Özellikleri](../xaml-services/namespace-language-features.md)
- [WPF XAML Uzantıları](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Temel Öğelere Genel Bakış](../../framework/wpf/advanced/base-elements-overview.md)
- [WPF İçinde Ağaçlar](../../framework/wpf/advanced/trees-in-wpf.md)
