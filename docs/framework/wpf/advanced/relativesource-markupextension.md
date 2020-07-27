---
title: RelativeSource MarkupExtension
description: Bir RelativeSource bağlama kaynağının özelliklerini, bir bağlama Işaretleme uzantısı içinde ya da XAML içindeki bir bağlamanın RelativeSource özelliğini ayarlarken belirtir.
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 2da702d23413651a85b45404e088f6708546cc25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165938"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Bağlama bir <xref:System.Windows.Data.RelativeSource> [Biçimlendirme Uzantısı](binding-markup-extension.md)içinde kullanılmak üzere veya <xref:System.Windows.Data.Binding.RelativeSource%2A> xaml 'de kurulu bir öğenin özelliği ayarlanırken bir bağlama kaynağının özelliklerini belirtir <xref:System.Windows.Data.Binding> .

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
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
|`modeEnumValue`|Aşağıdakilerden biri:<br /><br /> -Dize belirteci `Self` ;, <xref:System.Windows.Data.RelativeSource> öğesinin <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış olarak bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSourceMode.Self> .<br />-Dize belirteci `TemplatedParent` ;, <xref:System.Windows.Data.RelativeSource> öğesinin <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış olarak bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent> .<br />-Dize belirteci `PreviousData` ;, <xref:System.Windows.Data.RelativeSource> öğesinin <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği olarak ayarlanmış olarak bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSourceMode.PreviousData> .<br />-Mod hakkında bilgi için aşağıya bakın `FindAncestor` .|
|`FindAncestor`|Dize belirteci `FindAncestor` . Bu belirteci kullanmak `RelativeSource` , bir üst tür ve isteğe bağlı olarak bir üst düzeyi belirten bir mod girer. Bu, özelliği olarak ayarlanmış şekilde oluşturulmuş bir öğesine karşılık gelir <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> <xref:System.Windows.Data.RelativeSourceMode.FindAncestor> .|
|`typeName`|Mod için gereklidir `FindAncestor` . Özelliği dolduran bir türün adı <xref:System.Windows.Data.RelativeSource.AncestorType%2A> .|
|`intLevel`|Mod için isteğe bağlı `FindAncestor` . Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)|

## <a name="remarks"></a>Açıklamalar

`{RelativeSource TemplatedParent}`bağlama kullanımları, bir denetimin kullanıcı arabiriminin ve denetim mantığının ayrılma açısından daha büyük bir kavramı adresleyen bir anahtar tekniğidir. Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir. Bu durumda, [TemplateBinding Biçimlendirme Uzantısı](templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için bir toplu özelliktir: `{Binding RelativeSource={RelativeSource TemplatedParent}}` . `TemplateBinding`veya `{RelativeSource TemplatedParent}` kullanımları, yalnızca bir şablonu TANıMLAYAN XAML içinde ilgilidir. Daha fazla bilgi için bkz. [TemplateBinding Işaretleme uzantısı](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`, bir denetimin her zaman belirli bir üst türün görsel ağacında olması beklenildiği durumlarda denetim şablonlarında veya tahmin edilebilir kendiliğinden dahil edilen kullanıcı arabirimi kompozisyonlarında kullanılır. Örneğin, bir öğe denetiminin öğeleri `FindAncestor` kendi öğelerinin özelliklerine bağlamak için kullanımları kullanır üst üst öğe. Ya da bir şablonda denetim kompozisyonunun parçası olan öğeler, `FindAncestor` aynı bileşim yapısındaki üst öğelere bağlamaları kullanabilir.

XAML sözdizimi bölümlerinde gösterilen mod için nesne öğesi söz diziminde `FindAncestor` , ikinci nesne öğesi sözdizimi özellikle mod için kullanılır `FindAncestor` . `FindAncestor`mod bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değer gerektirir. <xref:System.Windows.Data.RelativeSource.AncestorType%2A>Aranacak üst öğe türüne bir [X:Type işaretleme uzantısı](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) başvurusu kullanarak bir öznitelik olarak ayarlamanız gerekir. <xref:System.Windows.Data.RelativeSource.AncestorType%2A>Değer, bağlama isteği çalışma zamanında işlendiğinde kullanılır.

`FindAncestor`Mod için, isteğe bağlı özelliği, <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> öğe ağacında var olan bir türün birden fazla üst öğesi olduğu durumlarda üst aramanın belirsizliğini ortadan kaldırmaya yardımcı olabilir.

Modunun nasıl kullanılacağı hakkında daha fazla bilgi için `FindAncestor` bkz <xref:System.Windows.Data.RelativeSource> ..

`{RelativeSource Self}`bir örneğin bir özelliğinin aynı örneğe ait başka bir özelliğin değerine bağlı olması gereken ve bu iki özellik arasında bir genel bağımlılık özelliği ilişkisi (zorlama gibi) olması gereken senaryolar için yararlıdır. Her iki özellik de değerler özdeş (ve özdeş olarak yazılmış) gibi bir nesne üzerinde mevcut olsa da, bir `Converter` bağlamaya parametre uygulayabilir `{RelativeSource Self}` ve kaynak ve hedef türleri arasında dönüştürme yapmak için dönüştürücüyü kullanabilirsiniz. İçin başka `{RelativeSource Self}` bir senaryo, bir parçasıdır <xref:System.Windows.MultiDataTrigger> .

Örneğin, aşağıdaki XAML, <xref:System.Windows.Shapes.Rectangle> için hangi değerin girildiğine bakılmaksızın bir öğesi tanımlar <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olur:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`veri şablonlarında ya da bağlamaların veri kaynağı olarak bir koleksiyon kullandığı durumlarda faydalıdır. `{RelativeSource PreviousData}`Koleksiyondaki bitişik veri öğeleri arasındaki ilişkileri vurgulamak için ' i kullanabilirsiniz. İlgili bir teknik, <xref:System.Windows.Data.MultiBinding> veri kaynağındaki geçerli ve önceki öğeler arasında bir bağlantı kurmak ve iki öğe ve özellikleri arasındaki farkı belirlemek için o bağlama üzerinde bir dönüştürücü kullanmaktır.

Aşağıdaki örnekte, <xref:System.Windows.Controls.TextBlock> öğeler şablonundaki ilk öğe geçerli sayıyı görüntüler. İkinci bağlama, genel olarak <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Data.MultiBinding> iki <xref:System.Windows.Data.Binding> anaykalara sahiptir: geçerli kayıt ve kullanarak önceki veri kaydını kullanan bir bağlama `{RelativeSource PreviousData}` . Ardından, üzerindeki bir dönüştürücü <xref:System.Windows.Data.MultiBinding> farkı hesaplar ve bağlamaya döndürür.

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
</ListBox>
```

Kavram olarak veri bağlamayı açıklamak burada ele alınmamalıdır, bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Xaml işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Data.RelativeSource> .

`RelativeSource`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML 'deki tüm biçimlendirme uzantıları, `{` `}` öznitelik sözdiziminde ve karakterlerini kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Bağlama Bildirimlerine Genel Bakış](../data/binding-declarations-overview.md)
- [x:Type İşaretleme Uzantısı](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
