---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 7a9c9fe379f361dec0d65b71c4d883958be9ed2f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834823"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension

Bir <xref:System.Windows.Data.RelativeSource> bağlama kaynağının özelliklerini, bir [bağlama Işaretleme uzantısı](binding-markup-extension.md)içinde kullanılmak üzere veya xaml 'de kurulu bir <xref:System.Windows.Data.Binding> öğesinin @no__t özelliğini ayarlarken belirler.

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

veya

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
|`modeEnumValue`|Aşağıdakilerden biri:<br /><br /> -@No__t-0; dize belirteci <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.Self> olarak ayarlanmış şekilde oluşturulan <xref:System.Windows.Data.RelativeSource> öğesine karşılık gelir.<br />-@No__t-0; dize belirteci <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent> olarak ayarlanmış şekilde oluşturulan <xref:System.Windows.Data.RelativeSource> öğesine karşılık gelir.<br />-@No__t-0; dize belirteci <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.PreviousData> olarak ayarlanmış şekilde oluşturulan <xref:System.Windows.Data.RelativeSource> öğesine karşılık gelir.<br />-@No__t-0 modu hakkında daha fazla bilgi için aşağıya bakın.|
|`FindAncestor`|@No__t-0 dize belirteci. Bu belirteci kullanmak `RelativeSource` ' ın bir üst türü ve isteğe bağlı olarak bir üst düzeyi belirttiğinden bir mod girer. Bu, <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliği <xref:System.Windows.Data.RelativeSourceMode.FindAncestor> olarak ayarlanmış şekilde oluşturulan <xref:System.Windows.Data.RelativeSource> ' a karşılık gelir.|
|`typeName`|@No__t-0 modu için gereklidir. @No__t-0 özelliğini dolduran bir türün adı.|
|`intLevel`|@No__t-0 modu için isteğe bağlı. Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)|

## <a name="remarks"></a>Açıklamalar

`{RelativeSource TemplatedParent}` bağlama kullanımları, bir denetimin kullanıcı arabiriminin ve denetim mantığının ayrılma açısından daha büyük bir kavramı adresleyen anahtar tekniğidir. Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir. Bu durumda, [TemplateBinding Biçimlendirme Uzantısı](templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için bir toplu özelliktir: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` veya `{RelativeSource TemplatedParent}` kullanımları, yalnızca bir şablonu tanımlayan XAML içinde ilgilidir. Daha fazla bilgi için bkz. [TemplateBinding Işaretleme uzantısı](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`, bir denetimin her zaman belirli bir üst türün görsel ağacında olması beklenildiği durumlar için genellikle denetim şablonlarında veya tahmin edilebilir kendiliğinden dahil edilen kullanıcı arabirimi kompozisyonlarında kullanılır. Örneğin, bir öğe denetiminin öğeleri kendi öğelerinin özelliklerine bağlamak için `FindAncestor` kullanımları kullanabilir. Ya da bir şablonda denetim kompozisyonunun parçası olan öğeler, aynı bileşim yapısındaki üst öğelere `FindAncestor` bağlamaları kullanabilir.

XAML sözdizimi bölümlerinde gösterilen `FindAncestor` modunun nesne öğesi söz diziminde, ikinci nesne öğesi sözdizimi özellikle `FindAncestor` modu için kullanılır. `FindAncestor` modu <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değeri gerektirir. Aranacak üst öğe türüne bir [X:Type Işaretleme uzantısı](../../xaml-services/x-type-markup-extension.md) başvurusu kullanarak bir öznitelik olarak <xref:System.Windows.Data.RelativeSource.AncestorType%2A> ayarlamanız gerekir. @No__t-0 değeri, bağlama isteği çalışma zamanında işlendiğinde kullanılır.

@No__t-0 modu için, isteğe bağlı özellik <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A>, öğe ağacında var olan bir türün birden fazla üst öğesi olduğu durumlarda üst aramanın belirsizliğini ortadan kaldırmaya yardımcı olabilir.

@No__t-0 modunun nasıl kullanılacağı hakkında daha fazla bilgi için, bkz. <xref:System.Windows.Data.RelativeSource>.

`{RelativeSource Self}`, bir örneğin bir özelliğinin aynı örneğe ait başka bir özelliğin değerine bağlı olması gereken ve bu iki özellik arasında (zorlama gibi) herhangi bir genel bağımlılık özelliği ilişkisinin zaten mevcut olduğu senaryolar için yararlıdır. Bir nesne üzerinde, değerlerin bire bir özdeş (ve özdeş olarak yazılmış) gibi iki özelliği var olsa da, `{RelativeSource Self}` içeren bir bağlamaya `Converter` parametresi uygulayabilir ve kaynak ve hedef türleri arasında dönüştürme yapmak için dönüştürücüyü kullanabilirsiniz. @No__t-0 ' a yönelik başka bir senaryo <xref:System.Windows.MultiDataTrigger> ' in bir parçasıdır.

Örneğin, aşağıdaki XAML, <xref:System.Windows.FrameworkElement.Width%2A> için hangi değerin girildiğine bakılmaksızın bir <xref:System.Windows.Shapes.Rectangle> öğesi tanımlar, <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olur: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`, veri şablonlarında ya da bağlamaların veri kaynağı olarak bir koleksiyon kullandığı durumlarda faydalıdır. Koleksiyondaki bitişik veri öğeleri arasındaki ilişkileri vurgulamak için `{RelativeSource PreviousData}` ' yı kullanabilirsiniz. İlgili bir teknik, veri kaynağındaki geçerli ve önceki öğeler arasında <xref:System.Windows.Data.MultiBinding> oluşturmak ve iki öğe ile özellikleri arasındaki farkı belirlemek için o bağlama üzerinde bir dönüştürücü kullanmaktır.

Aşağıdaki örnekte, öğeler şablonundaki ilk <xref:System.Windows.Controls.TextBlock> geçerli sayıyı görüntüler. İkinci <xref:System.Windows.Controls.TextBlock> bağlama, aday olarak iki <xref:System.Windows.Data.Binding> ' ye sahip olan bir <xref:System.Windows.Data.MultiBinding> ' dir: geçerli kayıt ve `{RelativeSource PreviousData}` ' i kullanarak bir önceki veri kaydını kasıtlı olarak kullanan bir bağlama. Sonra, <xref:System.Windows.Data.MultiBinding> üzerindeki bir dönüştürücü farkı hesaplar ve bağlamaya döndürür.

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

Kavram olarak veri bağlamayı açıklamak burada ele alınmamalıdır, bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

@No__t-0 XAML işlemci uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Data.RelativeSource> sınıfı tarafından tanımlanır.

`RelativeSource` bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML 'deki tüm biçimlendirme uzantıları, öznitelik sözdiziminde `{` ve `}` karakterlerini kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Bağlama Bildirimlerine Genel Bakış](../data/binding-declarations-overview.md)
- [x:Type İşaretleme Uzantısı](../../xaml-services/x-type-markup-extension.md)
