---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: d96a00afc08f2c5593dad5a3a47ab46045ff6b0f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365119"
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension
Özelliklerini belirtir bir <xref:System.Windows.Data.RelativeSource> içinde kullanılacak bağlama kaynağı, bir [Binding Markup Extension](binding-markup-extension.md), veya ayarlarken <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliği bir <xref:System.Windows.Data.Binding> XAML içinde oluşturulmuş bir öğe.  
  
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
|`modeEnumValue`|Aşağıdakilerden biri:<br /><br /> -Dize belirteci `Self`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Dize belirteci `TemplatedParent`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Dize belirteci `PreviousData`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Aşağıda hakkında bilgi için `FindAncestor` modu.|  
|`FindAncestor`|Dize belirteci `FindAncestor`. Bu belirteci kullanarak moda girer bir `RelativeSource` 'un üst türü ve isteğe bağlı olarak üst düzeyini belirtir. Bu karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|  
|`typeName`|Gerekli `FindAncestor` modu. Dolduran bir türün adını <xref:System.Windows.Data.RelativeSource.AncestorType%2A> özelliği.|  
|`intLevel`|İçin isteğe bağlı `FindAncestor` modu. Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)|  
  
## <a name="remarks"></a>Açıklamalar  
 `{RelativeSource TemplatedParent}` bağlama kullanımları, denetime ait kullanıcı ve denetim mantığının ayrımı daha büyük bir kavramı ele alan önemli bir tekniktir. Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir. Bu durum için [TemplateBinding Markup Extension](templatebinding-markup-extension.md) aslında şu bağlama ifadesi için bir toplu olduğu: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` veya `{RelativeSource TemplatedParent}` kullanımları, her ikisi de, bir şablon tanımlayan XAML içinde yalnızca ilgilidir. Daha fazla bilgi için [TemplateBinding işaretleme uzantısı](templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}` esas olarak denetim şablonları veya öngörülebilir kendi kullanıcı Arabirimi bileşimlerinde, burada bir denetimi her zaman belirli bir üst öğe türünün görsel ağacında olması beklenen durumlarda kullanılır. Örneğin, bir öğeler denetiminin öğeleri kullanabilirsiniz `FindAncestor` öğelerin özelliklerine bağlanacağını kullanımları üst üst denetim. Veya bir şablonda denetim bileşiminin parçası olan öğeler kullanabileceğiniz `FindAncestor` , aynı bileşim yapısı içinde üst öğelere bağlar.  
  
 Nesne öğesi sözdizimi içinde `FindAncestor` ikinci nesne öğesi sözdizimi özellikle için kullanılan XAML sözdizimi bölümlerinde gösterilen modu `FindAncestor` modu. `FindAncestor` mod gerektirir bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değeri. Ayarlamalısınız <xref:System.Windows.Data.RelativeSource.AncestorType%2A> kullanarak bir özniteliği olarak bir [x: Type işaretleme uzantısı](../../xaml-services/x-type-markup-extension.md) Aranılacak türü referansı. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Değeri, bağlama isteği çalışma zamanında işlendiğinde kullanılır.  
  
 İçin `FindAncestor` modu, isteğe bağlı özellik <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> durumlarda üst arama belirsizliğinin ortadan kaldırılmasını yardımcı olabilecek birden fazla üst öğe ağacında varolan bu türün büyük olasılıkla olduğu.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `FindAncestor` modu bkz <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}` senaryolarda yararlıdır bu iki özellik arasında var. burada örnek bir özellik aynı örneğini ve hiçbir genel bağımlılık özelliği ilişkisi (zorlama gibi) başka bir özelliğin değerini zaten bağlı olmamalıdır. İki özellik mevcut bir nesne üzerinde değerleri değişmez olarak aynı olacak (ve aynı şekilde), ayrıca uygulayabilirsiniz nadir olmasına rağmen bir `Converter` parametresi içeren bir bağlamaya `{RelativeSource Self}`ve kaynak arasında dönüştürmek için dönüştürücüyü kullanabilirsiniz ve Hedef türü. Başka bir senaryo için `{RelativeSource Self}` parçası olarak bir <xref:System.Windows.MultiDataTrigger>.  
  
 Örneğin, aşağıdaki XAML tanımlayan bir <xref:System.Windows.Shapes.Rectangle> hangi değer için girilen öğesi böyle <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olacağı: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}` Veri şablonları veya bağlamaları veri kaynağı olarak bir koleksiyon burada kullanıyorsanız durumlarda yararlı olur. Kullanabileceğiniz `{RelativeSource PreviousData}` koleksiyondaki bitişik veri öğeleri arasındaki ilişkileri vurgulamak için. İlgili bir teknik bir <xref:System.Windows.Data.MultiBinding> veri kaynağı ve iki öğe ve özellikleri arasındaki farkı belirlemek için bu bağlama üzerinde bir dönüştürücü geçerli ve önceki öğeler arasında.  
  
 Aşağıdaki örnekte, ilk <xref:System.Windows.Controls.TextBlock> öğeleri şablon geçerli sayıyı gösterir. İkinci <xref:System.Windows.Controls.TextBlock> bağlamanın bir <xref:System.Windows.Data.MultiBinding> iki olup sahip <xref:System.Windows.Data.Binding> bileşenine sahiptir: geçerli kayıt ve kullanarak, önceki veri kaydını kasıtlı olarak kullanan bir bağlama `{RelativeSource PreviousData}`. Ardından, üzerinde bir dönüştürücü <xref:System.Windows.Data.MultiBinding> farkı hesaplar ve bağlamaya geri döndürür.  
  
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
  
 Bir kavram, burada kapsanmayan olarak veri bağlamasını açıklama bkz [Data Binding Overview](../data/data-binding-overview.md).  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.Data.RelativeSource> sınıfı.  
  
 `RelativeSource` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML kullanım içindeki tüm biçimlendirme uzantıları `{` ve `}` karakter olarak bir XAML işlemcisinin bir işaretleme uzantısı özniteliği işlenmesi gerektiğini, kuralına göre kendi öznitelik sözdizimi. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Data.Binding>
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Bağlama Bildirimlerine Genel Bakış](../data/binding-declarations-overview.md)
- [x:Type İşaretleme Uzantısı](../../xaml-services/x-type-markup-extension.md)
