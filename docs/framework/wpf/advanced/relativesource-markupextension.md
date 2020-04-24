---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646225"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

[Bağlayıcı Biçimlendirme](binding-markup-extension.md)Uzantısı <xref:System.Windows.Data.RelativeSource> içinde veya XAML'de kurulan bir <xref:System.Windows.Data.Binding> öğenin <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliğini ayarlarken kullanılacak bağlayıcı kaynağın özelliklerini belirtir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

-veya-

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`modeEnumValue`|Aşağıdakilerden biri:<br /><br /> - Dize `Self`belirteci ; olarak oluşturulan <xref:System.Windows.Data.RelativeSource> bir <xref:System.Windows.Data.RelativeSource.Mode%2A> özellik için <xref:System.Windows.Data.RelativeSourceMode.Self>ayarlanır karşılık gelir.<br />- Dize `TemplatedParent`belirteci ; olarak oluşturulan <xref:System.Windows.Data.RelativeSource> bir <xref:System.Windows.Data.RelativeSource.Mode%2A> özellik için <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>ayarlanır karşılık gelir.<br />- Dize `PreviousData`belirteci ; olarak oluşturulan <xref:System.Windows.Data.RelativeSource> bir <xref:System.Windows.Data.RelativeSource.Mode%2A> özellik için <xref:System.Windows.Data.RelativeSourceMode.PreviousData>ayarlanır karşılık gelir.<br />- Mod hakkında `FindAncestor` bilgi için aşağıya bakın.|
|`FindAncestor`|Dize belirteci. `FindAncestor` Bu belirteç kullanarak bir `RelativeSource` ata türü ve isteğe bağlı olarak bir ata düzeyi belirtir bir mod girer. Bu, kendi <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış bir <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>olarak karşılık gelir.|
|`typeName`|Mod `FindAncestor` için gereklidir. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Özelliği dolduran bir türün adı.|
|`intLevel`|Mod `FindAncestor` için isteğe bağlıdır. Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)|

## <a name="remarks"></a>Açıklamalar

`{RelativeSource TemplatedParent}`bağlama kullanımları, bir denetimin UI'sinin ve denetimin mantığının ayrılmasıyla ilgili daha büyük bir kavramı ele alan önemli bir tekniktir. Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir. Bu durumda, [TemplateBinding Biçimlendirme Uzantısı](templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için `{Binding RelativeSource={RelativeSource TemplatedParent}}`bir kısaltmadır: . `TemplateBinding`veya `{RelativeSource TemplatedParent}` kullanımlar yalnızca şablon tanımlayan XAML içinde alakalıdır. Daha fazla bilgi için [Bkz. TemplateBinding Biçimlendirme Uzantısı.](templatebinding-markup-extension.md)

`{RelativeSource FindAncestor}`denetimin her zaman belirli bir ata türündeki görsel bir ağaçta olması beklenen durumlarda, çoğunlukla denetim şablonlarında veya öngörülebilir bağımsız kullanıcı arabirimi kompozisyonlarında kullanılır. Örneğin, bir öğe denetimi öğeleri, öğeleri denetim üst atalarının özelliklerine bağlamak için kullanımları kullanabilirsiniz. `FindAncestor` Veya, bir şablondaki denetim kompozisyonunun bir `FindAncestor` parçası olan öğeler, aynı kompozisyon yapısındaki ana öğelere bağlamaları kullanabilir.

XAML Sözdizimi `FindAncestor` bölümlerinde gösterilen mod için nesne öğesi sözdiziminde, ikinci `FindAncestor` nesne öğesi sözdizimi özellikle mod için kullanılır. `FindAncestor`modu bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değer gerektirir. Bir öznitelik olarak <xref:System.Windows.Data.RelativeSource.AncestorType%2A> [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) başvuruiçin ata türü aramak için bir öznitelik olarak ayarlamanız gerekir. Değer, <xref:System.Windows.Data.RelativeSource.AncestorType%2A> bağlama isteği çalışma zamanında işlendiğinde kullanılır.

Mod `FindAncestor` için, isteğe bağlı özellik, <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> öğe ağacında var olan bu türde birden fazla atanın bulunduğu durumlarda ata nın aramasını ayrıştırmada yardımcı olabilir.

`FindAncestor` Modun nasıl kullanılacağı hakkında daha <xref:System.Windows.Data.RelativeSource>fazla bilgi için bkz.

`{RelativeSource Self}`bir örneğin bir özelliğinin aynı örneğin başka bir özelliğinin değerine bağlı olması ve bu iki özellik arasında genel bağımlılık özelliği ilişkisinin (zorlama gibi) zaten bulunmadığı senaryolar için yararlıdır. Değerlerin tam anlamıyla aynı olduğu (ve aynı şekilde yazılmış) bir nesne üzerinde iki özelliğin `Converter` bulunması nadir olsa `{RelativeSource Self}`da, kaynak ve hedef türleri arasında dönüştürme yapmak için dönüştürücükullanan bir bağlayıcıya bir parametre de uygulayabilirsiniz. Başka bir `{RelativeSource Self}` senaryo için <xref:System.Windows.MultiDataTrigger>bir parçası olarak .

Örneğin, aşağıdaki XAML, hangi <xref:System.Windows.Shapes.Rectangle> değer için <xref:System.Windows.FrameworkElement.Width%2A>girilirse girilen bir öğeyi tanımlar, her zaman bir <xref:System.Windows.Shapes.Rectangle> karedir:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`veri şablonlarında veya bağlayıcıların bir koleksiyonu veri kaynağı olarak kullandığı durumlarda yararlıdır. Koleksiyondaki `{RelativeSource PreviousData}` bitişik veri öğeleri arasındaki ilişkileri vurgulamak için kullanabilirsiniz. İlgili bir teknik, <xref:System.Windows.Data.MultiBinding> veri kaynağındaki geçerli ve önceki öğeler arasında bir öğe oluşturmak ve iki öğe ile özellikleri arasındaki farkı belirlemek için bu bağlayıcıüzerinde bir dönüştürücü kullanmaktır.

Aşağıdaki örnekte, öğeler <xref:System.Windows.Controls.TextBlock> şablonundaki ilk geçerli sayı görüntülenir. İkinci <xref:System.Windows.Controls.TextBlock> bağlama nominal <xref:System.Windows.Data.MultiBinding> olarak iki <xref:System.Windows.Data.Binding> bileşeni olan birdir: geçerli kayıt ve önceki veri kaydını `{RelativeSource PreviousData}`kullanarak kasıtlı olarak kullanan bir bağlama. Daha sonra, bir <xref:System.Windows.Data.MultiBinding> dönüştürücü farkı hesaplar ve bağlama döndürür.

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
```

Veri bağlamayı bir kavram olarak açıklayan burada ele alınmaz, [bkz.](../../../desktop-wpf/data/data-binding-overview.md)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.Data.RelativeSource> sınıf tarafından tanımlanır.

`RelativeSource`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML'deki tüm biçimlendirme `{` uzantıları, bir XAML işlemcinin bir biçimlendirme uzantısıözözelliği ni işlemesi gerektiğini kabul ettiği kural olan öznitelik sözdiziminde karakterleri ve `}` karakterleri kullanır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağlama Bildirimlerine Genel Bakış](../data/binding-declarations-overview.md)
- [x:Type İşaretleme Uzantısı](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
